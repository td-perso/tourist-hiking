<template>
  <div>
    <h1>Circuit Test</h1>
    <div ref="map" style="width: 100%; height: 500px" />
    <button @click="launchNavigation">
      Lancer la navigation
    </button>
  </div>
</template>

<script>
  import { DOMParser } from 'xmldom'
  import { gpx } from '@mapbox/togeojson'

  export default {
    name: 'CircuitTest',
    data () {
      return {
        map: null,
        directionsService: null,
        directionsRenderer: null,
        googleMapsUrl: '',
        startCoords: null,
        endCoords: null,
        waypoints: [],
      }
    },
    async mounted () {
      await this.loadGpxFile()
      this.loadGoogleMapsApi()
    },
    methods: {
      loadGoogleMapsApi () {
        const script = document.createElement('script')
        script.src = `https://maps.googleapis.com/maps/api/js?key=AIzaSyDhKUsMHr-v02bPvK28vkF95fzNky3KB2s&callback=initMap`
        script.async = true
        script.defer = true
        window.initMap = this.initMap
        document.head.appendChild(script)
      },
      initMap () {
        this.map = new google.maps.Map(this.$refs.map, {
          zoom: 12,
          center: this.startCoords,
        })
        this.directionsService = new google.maps.DirectionsService()
        this.directionsRenderer = new google.maps.DirectionsRenderer({
          map: this.map,
        })
        this.calculateAndDisplayRoute()
      },
      async loadGpxFile () {
        const response = await fetch('/tourist-hiking/data/circuit.gpx') // Mettez ici le chemin vers votre fichier GPX
        const gpxData = await response.text()
        const parser = new DOMParser()
        const xmlDoc = parser.parseFromString(gpxData, 'application/xml')
        const geojson = gpx(xmlDoc)
        const waypoints = geojson.features[0].geometry.coordinates.map(coord => ({
          lat: coord[1],
          lng: coord[0],
        }))
        this.startCoords = waypoints[0]
        this.endCoords = waypoints[waypoints.length - 1]
        this.waypoints = waypoints.slice(1, -1).map(point => ({
          location: point,
          stopover: true,
        }))
        this.googleMapsUrl = this.generateGoogleMapsUrl(this.startCoords, this.endCoords, this.waypoints)
      },
      generateGoogleMapsUrl (start, end, waypoints) {
        const baseUrl = 'https://www.google.com/maps/dir/'
        const startCoords = `${start.lat},${start.lng}`
        const endCoords = `${end.lat},${end.lng}`
        const waypointsStr = waypoints.map(wp => `${wp.location.lat},${wp.location.lng}`).join('/')
        return `${baseUrl}${startCoords}/${waypointsStr}/${endCoords}`
      },
      calculateAndDisplayRoute () {
        this.directionsService.route(
          {
            origin: this.startCoords,
            destination: this.endCoords,
            waypoints: this.waypoints,
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
      isMobile () {
        return /Android|webOS|iPhone|iPad|iPod|BlackBerry|IEMobile|Opera Mini/i.test(navigator.userAgent)
      },
      launchNavigation () {
        if (this.isMobile()) {
          const stops = this.waypoints.map(wp => `via:${wp.location.lat},${wp.location.lng}`).join('/')
          const url = `google.navigation:q=${this.endCoords.lat},${this.endCoords.lng}&waypoints=${stops}`
          window.open(url, '_blank')
        } else {
          window.open(this.googleMapsUrl, '_blank')
        }
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
