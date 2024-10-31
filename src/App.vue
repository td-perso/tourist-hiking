<template>
  <v-app>
    <v-main>
      <router-view class="router-view-background" />
    </v-main>
  </v-app>
</template>

<script lang="ts" setup>
//
</script>
<style scoped>
.router-view-background {
  background-color: white; /* Changez cette couleur selon vos besoins */
  /* min-height: 100vh;  */
}
</style>
