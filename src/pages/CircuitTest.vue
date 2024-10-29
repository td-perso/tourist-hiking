<template>
  <div>
    <main>
      <h1>Circuit Test</h1>
      <div id="map" ref="map" style="height: 500px;" />
      <button @click="launchNavigation">
        Lancer la navigation
      </button>
    </main>
  </div>
</template>

<script>
  import { DOMParser } from 'xmldom'
  import { gpx } from '@mapbox/togeojson'

  export default {
    name: 'CircuitTest',
    data () {
      return {
        googleMapsUrl: '',
        map: null,
        directionsService: null,
        directionsRenderer: null,
        startCoords: null,
        endCoords: null,
        waypoints: [],
      }
    },
    async mounted () {
      window.initMap = this.initMap
      this.loadGoogleMapsApi()
      await this.loadGpxFile()
    },
    methods: {
      loadGoogleMapsApi () {
        const script = document.createElement('script')
        script.src = `https://maps.googleapis.com/maps/api/js?key=AIzaSyDhKUsMHr-v02bPvK28vkF95fzNky3KB2s&libraries=geometry,places,drawing&callback=initMap`
        script.async = true
        script.defer = true
        document.head.appendChild(script)
      },
      initMap () {
        this.map = new google.maps.Map(this.$refs.map, {
          zoom: 12,
          center: { lat: 48.8588443, lng: 2.2943506 }, // Coordonnées par défaut
        })
        this.directionsService = new google.maps.DirectionsService()
        this.directionsRenderer = new google.maps.DirectionsRenderer({
          map: this.map,
        })
      },
      async loadGpxFile () {
        const response = await fetch('https://www.google.com/maps/d/edit?mid=1i5Jaw01smoDwoNUcR4azUsic_1jqmK4&usp=sharing') // Mettez ici le chemin vers votre fichier GPX
        const gpxData = await response.text()
        const parser = new DOMParser()
        const xmlDoc = parser.parseFromString(gpxData, 'application/xml')
        const geojson = gpx(xmlDoc)
        const waypoints = geojson.features[0].geometry.coordinates
        this.startCoords = { lat: waypoints[0][1], lng: waypoints[0][0] }
        this.endCoords = { lat: waypoints[waypoints.length - 1][1], lng: waypoints[waypoints.length - 1][0] }
        this.waypoints = waypoints.slice(1, -1).map(point => ({
          location: { lat: point[1], lng: point[0] },
          stopover: true,
        }))
        this.googleMapsUrl = this.generateGoogleMapsUrl(this.startCoords, this.endCoords, this.waypoints)
        this.calculateAndDisplayRoute(this.startCoords, this.endCoords, this.waypoints)
      },
      generateGoogleMapsUrl (start, end, waypoints) {
        const baseUrl = 'https://www.google.com/maps/dir/'
        const startCoords = `${start.lat},${start.lng}`
        const endCoords = `${end.lat},${end.lng}`
        const waypointsStr = waypoints.map(wp => `${wp.location.lat},${wp.location.lng}`).join('/')
        return `${baseUrl}${startCoords}/${waypointsStr}/${endCoords}`
      },
      calculateAndDisplayRoute (start, end, waypoints) {
        this.directionsService.route(
          {
            origin: start,
            destination: end,
            waypoints,
            travelMode: google.maps.TravelMode.DRIVING,
          },
          (response, status) => {
            if (status === 'OK') {
              this.directionsRenderer.setDirections(response)
            } else {
              console.error('Directions request failed due to ' + status)
            }
          }
        )
      },
      launchNavigation () {
        window.open(this.googleMapsUrl, '_blank')
      },
    },
  }
</script>

<style scoped>
/* Styles spécifiques au composant */
#map {
  height: 500px;
}
</style>
