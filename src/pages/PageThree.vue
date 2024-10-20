<template>
  <div>
    <AppHeader />
    <main>
      <h1>Page Three</h1>
    </main>
    <AppFooter />
  </div>
</template>

<script>
  import AppHeader from '@/components/AppHeader.vue'
  import AppFooter from '@/components/AppFooter.vue'

  export default {
    name: 'PageThree',
    components: {
      AppHeader,
      AppFooter,
    },
  }
</script>

<style scoped>
/* Add your styles here */
</style>
