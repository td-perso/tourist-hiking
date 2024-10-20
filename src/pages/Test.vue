<template>
  <div>
    <a :href="googleMapsUrl" target="_blank">Lancer la navigation</a>
  </div>
</template>

<script>
  import { DOMParser } from 'xmldom'
  import { gpx } from '@mapbox/togeojson'

  export default {
    data () {
      return {
        googleMapsUrl: '',
      }
    },
    mounted () {
      this.loadGpxFile()
    },
    methods: {
      async loadGpxFile () {
        const response = await fetch('/tourist-hiking/data/circuit.gpx')
        const gpxData = await response.text()
        const parser = new DOMParser()
        const xmlDoc = parser.parseFromString(gpxData, 'application/xml')
        const geojson = gpx(xmlDoc)

        const waypoints = geojson.features[0].geometry.coordinates
        const start = waypoints[0]
        const end = waypoints[waypoints.length - 1]
        const waypointsCoords = waypoints.slice(1, waypoints.length - 1).map(point => `${point[1]},${point[0]}`)

        this.googleMapsUrl = this.generateGoogleMapsUrl(start, end, waypointsCoords)
      },
      generateGoogleMapsUrl (start, end, waypoints) {
        const baseUrl = 'https://www.google.com/maps/dir/'
        const startCoords = `${start[1]},${start[0]}`
        const endCoords = `${end[1]},${end[0]}`
        const waypointsStr = waypoints.join('/')
        return `${baseUrl}${startCoords}/${waypointsStr}/${endCoords}`
      },
    },
  }
</script>
