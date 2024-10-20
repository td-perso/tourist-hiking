<template>
  <v-footer app>
    <v-col class="d-flex justify-center align-center">
      <v-img max-height="50" max-width="50" src="@/assets/flag.png" />
      {{ new Date().getFullYear() }} — <strong>{{ appVersion }}</strong>
    </v-col>
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
