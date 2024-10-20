<template>
  <div>
    <AppHeader />
    <main>
      <h1>Page One</h1>
    </main>
    <AppFooter />
  </div>
</template>

<script>
  import AppHeader from '@/components/AppHeader.vue'
  import AppFooter from '@/components/AppFooter.vue'

  export default {
    name: 'PageOne',
    components: {
      AppHeader,
      AppFooter,
    },
  }
</script>

<style scoped>
/* Add your styles here */
</style>
