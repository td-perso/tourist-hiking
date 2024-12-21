<template>
  <div id="map" />
</template>

<script>
  import L from 'leaflet'
  import 'leaflet/dist/leaflet.css'
  import 'leaflet.markercluster/dist/MarkerCluster.css'
  import 'leaflet.markercluster/dist/MarkerCluster.Default.css'
  import 'leaflet.markercluster'

  export default {
    name: 'MapComponent',
    data () {
      return {
        map: null,
        pointsDePassage: [
          { lat: 48.8588443, lng: 2.2943506 }, // Exemple de coordonnées
        // Ajoutez d'autres points de passage ici
        ],
        pointsDInteret: [
          { lat: 48.8588443, lng: 2.2943506, label: '1' },
          { lat: 48.8588443, lng: 2.3043506, label: '2' },
          { lat: 48.8588443, lng: 2.3143506, label: '3' },
        // Ajoutez d'autres points d'intérêt ici
        ],
      }
    },
    mounted () {
      this.initMap()
    },
    methods: {
      initMap () {
        this.map = L.map('map').setView([48.8588443, 2.2943506], 12)

        L.tileLayer('https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png', {
          attribution: '&copy; OpenStreetMap contributors',
        }).addTo(this.map)

        this.addPointsDePassage()
        this.addPointsDInteret()
      },
      addPointsDePassage () {
        this.pointsDePassage.forEach(point => {
          L.marker([point.lat, point.lng], {
            icon: L.icon({
              iconUrl: 'http://leafletjs.com/examples/custom-icons/leaf-green.png',
              shadowUrl: 'http://leafletjs.com/examples/custom-icons/leaf-shadow.png',
              iconSize: [38, 95], // taille de l'icône
              shadowSize: [50, 64], // taille de l'ombre
              iconAnchor: [22, 94], // point d'ancrage de l'icône
              shadowAnchor: [4, 62], // point d'ancrage de l'ombre
              popupAnchor: [-3, -76], // point d'ancrage de la popup relative à l'icône
            }),
          }).addTo(this.map)
        })
      },
      addPointsDInteret () {
        const markers = L.markerClusterGroup()

        this.pointsDInteret.forEach(point => {
          const marker = L.marker([point.lat, point.lng], {
            icon: L.divIcon({
              className: 'custom-icon',
              html: `<div style="background-color: #2A9FD6; color: white; border-radius: 50%; width: 24px; height: 24px; display: flex; align-items: center; justify-content: center;">${point.label}</div>`,
            }),
          })
          markers.addLayer(marker)
        })

        this.map.addLayer(markers)
      },
    },
  }
</script>

<style scoped>
#map {
  height: 100vh;
  width: 100%;
}
</style>
