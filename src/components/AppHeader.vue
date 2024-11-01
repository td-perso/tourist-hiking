<template>
  <div>
    <v-navigation-drawer v-model="drawer" temporary>
      <v-list-item
        link
        prepend-icon="mdi-close"
        title="Fermer"
        @click="drawer = false"
      />
      <v-divider />
      <v-list v-model="selectedItem" color="primary" flat>
        <v-list-item
          v-for="(item, i) in items"
          :key="i"
          link
          :prepend-icon="item.icon"
          :subtitle="item.subtitle"
          :title="item.text"
          :to="item.to"
        />
      </v-list>
      <template #append>
        <v-divider />
        <div class="pa-2">
          <v-btn block color="red" dark @click="logout">
            <v-icon>mdi-logout</v-icon> Logout
          </v-btn>
        </div>
      </template>
    </v-navigation-drawer>
    <v-app-bar color="white">
      <v-app-bar-nav-icon @click="drawer = !drawer" />
      <v-toolbar-title>
        <h1 class="title d-flex justify-center align-center text-h5 text-md-h4 text-lg-h4 text-xl-h4">
          <router-link class="title-link" to="Index">
            Les Circuits de Constantine
          </router-link>
        </h1>
      </v-toolbar-title>
      <v-img max-height="50" max-width="50" src="@/assets/logo.png" />
    </v-app-bar>
  </div>
</template>

<script>
  export default {
    name: 'AppHeader',
    data: () => ({
      drawer: false,
      selectedItem: 1,
      items: [
        { text: 'Accueil', icon: 'mdi-home', to: 'Index' },
        { text: 'Circuit 1', subtitle: 'Nom du circuit 1', icon: 'mdi-walk', to: 'CircuitOne' },
        { text: 'Circuit 2', subtitle: 'Nom du circuit 2', icon: 'mdi-bike', to: 'CircuitTwo' },
        { text: 'Circuit 3', subtitle: 'Nom du circuit 3', icon: 'mdi-car-side', to: 'CircuitThree' },
        { text: 'Circuit Test', icon: 'mdi-bus-side', to: 'CircuitTest' },
      ],
    }),
    methods: {
      logout () {
        this.$router.push('connexion')
      },
    },
  }
</script>

<style scoped>
.title-link {
  text-decoration: none;
  color: inherit;
}
.title {
  font-family: 'Great Vibes', cursive;
  color: #176535;
  /* font-weight: bold; */
}
</style>
