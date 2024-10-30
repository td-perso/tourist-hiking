<template>
  <div>
    <h1>Circuit Test</h1>
    <iframe
      allowfullscreen
      frameborder="0"
      height="500"
      :src="mapUrl"
      width="100%"
    />
    <button @click="launchNavigation">
      Lancer la navigation
    </button>
  </div>
</template>

<script>
  export default {
    name: 'CircuitTest',
    data () {
      return {
        mapUrl: 'https://www.google.com/maps/embed?pb=!1m58!1m12!1m3!1d6422.671032568122!2d6.658426144593031!3d36.401076924931715!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!4m43!3e2!4m3!3m2!1d36.3958911!2d6.6565435!4m3!3m2!1d36.396466499999995!2d6.6599981999999995!4m3!3m2!1d36.397351199999996!2d6.6649236!4m3!3m2!1d36.3992887!2d6.666050599999999!4m3!3m2!1d36.402245199999996!2d6.6675255!4m3!3m2!1d36.404888!2d6.6704612!4m3!3m2!1d36.4058399!2d6.6690838!4m3!3m2!1d36.4027379!2d6.6668854!4m3!3m2!1d36.4013829!2d6.6647427!4m5!1s0x12f17671baf6f649%3A0x43d3c87c2572968!2sConstantine!3m2!1d36.3958817!2d6.656253899999999!5e0!3m2!1sen!2suk!4v1730243347749!5m2!1sen!2suk',
        endCoords: null,
        waypoints: [],
      }
    },
    mounted () {
      this.extractCoordinatesFromUrl()
    },
    methods: {
      extractCoordinatesFromUrl () {
        const url = new URL(this.mapUrl)
        const params = url.searchParams.get('pb')
        const coords = [...params.matchAll(/!3m2!1d([\d.-]+)!2d([\d.-]+)/g)].map(match => ({
          lat: parseFloat(match[1]),
          lng: parseFloat(match[2]),
        }))
        this.endCoords = coords.pop()
        this.waypoints = coords
      },
      isMobile () {
        return /Android|webOS|iPhone|iPad|iPod|BlackBerry|IEMobile|Opera Mini/i.test(navigator.userAgent)
      },
      launchNavigation () {
        if (this.isMobile()) {
          navigator.geolocation.getCurrentPosition(
            position => {
              const origin = `${position.coords.latitude},${position.coords.longitude}`
              const destination = `${this.endCoords.lat},${this.endCoords.lng}`

              // Le format "geo:" avec des coordonnées de destination et une chaîne de requête
              const waypointsString = this.waypoints.map(wp => `${wp.lat},${wp.lng}`).join(';')

              const geoUrl = `geo:0,0?q=${destination}(${encodeURIComponent('Destination')})&waypoints=${waypointsString}`

              // Ouvrir le lien en espérant que cela lance l'application Google Maps
              window.location.href = geoUrl
            },
            error => {
              console.error('Erreur lors de la récupération de la position', error)
              alert('Impossible de récupérer votre position actuelle pour lancer la navigation.')
            }
          )
        } else {
          // Fallback pour le navigateur desktop
          const origin = 'My+Location'
          const destination = `${this.endCoords.lat},${this.endCoords.lng}`
          const waypoints = this.waypoints.map(wp => `${wp.lat},${wp.lng}`).join('|')
          const url = `https://www.google.com/maps/dir/?api=1&origin=${origin}&destination=${destination}&waypoints=${waypoints}`
          window.open(url, '_blank')
        }
      },
    },
  }
</script>

<style scoped>
/* Styles spécifiques au composant */
</style>
