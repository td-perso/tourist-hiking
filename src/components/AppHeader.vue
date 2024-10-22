<template>
  <div>
    <v-navigation-drawer v-model="drawer" app>
      <v-list v-model="selectedItem" color="primary" flat>
        <v-list-item v-for="(item, i) in items" :key="i" link :to="item.to">
          <v-icon>{{ item.icon }}</v-icon>
          <v-list-item-title>{{ item.text }}</v-list-item-title>
        </v-list-item>
      </v-list>
      <template #append>
        <div class="pa-2">
          <v-btn block color="red" dark @click="logout">
            <v-icon>mdi-logout</v-icon> Logout
          </v-btn>
        </div>
      </template>
    </v-navigation-drawer>
    <v-app-bar app>
      <v-app-bar-nav-icon @click="drawer = !drawer" />
      <v-spacer />
      <v-toolbar-title>
        <h1 class="title">
          Les circuits de Constantine
        </h1>
      </v-toolbar-title>
      <v-spacer />
      <v-img max-height="50" max-width="50" src="@/assets/logo.png" />
    </v-app-bar>
  </div>
</template>

<script>
  export default {
    name: 'AppHeader',
    components: {},
    data: () => ({
      drawer: false,
      selectedItem: 1,
      items: [
        { text: 'Accueil', icon: 'mdi-home', to: 'Index' },
        { text: 'Circuit 1', icon: 'mdi-arrow-right-box', to: 'CircuitOne' },
        { text: 'Circuit 2', icon: 'mdi-arrow-right-box', to: 'CircuitTwo' },
        { text: 'Circuit 3', icon: 'mdi-arrow-right-box', to: 'CircuitThree' },
        { text: 'Circuit Test', icon: 'mdi-arrow-right-box', to: 'CircuitTest' },
      ],
    }),
    computed: {
    },
    methods: {
      logout () {
        this.$router.push('connexion')
      },
    },
  }
</script>

<style scoped>
.disable-events {
  pointer-events: none;
}
.title {
  font-family: 'Send Flowers', cursive;
  font-size: 30px;
}
</style>
