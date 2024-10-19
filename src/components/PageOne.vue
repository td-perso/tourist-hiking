<template>
  <div class="page-one">
    <h1>Welcome to Page One</h1>
    <p>This is a sample Vue component.</p>
  </div>
</template>

<script>
  export default {
    name: 'PageOne',
    data () {
      return {
        message: 'Hello, Vue!',
      }
    },
  }
</script>

<style scoped>
.page-one {
  text-align: center;
  margin-top: 50px;
}
</style>
