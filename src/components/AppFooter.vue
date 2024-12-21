<template>
  <v-footer app class="d-flex flex-column" color="#362f2d">
    <div class="d-flex w-100 justify-center align-center">
      <v-img max-height="50" max-width="50" src="@/assets/flag.png" />
    </div>
  </v-footer>
</template>

<script>
  import { version } from '../../package.json'

  export default {
    name: 'AppFooter',
    data () {
      return {
        appVersion: version,
      }
    },
  }
</script>

<style scoped>
/* Styles spécifiques au composant */
</style>
