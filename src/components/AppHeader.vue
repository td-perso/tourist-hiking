<template>
  <div>
    <v-navigation-drawer v-model="drawer">
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
    <v-app-bar>
      <v-app-bar-nav-icon @click="drawer = !drawer" />
      <v-spacer />
      <v-toolbar-title>
        <h1 class="title">
          Les Circuits de Constantine
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
        { text: 'Circuit 1', subtitle: 'Nom du circuit 1', icon: 'mdi-walk', to: 'CircuitOne' },
        { text: 'Circuit 2', subtitle: 'Nom du circuit 2', icon: 'mdi-bike', to: 'CircuitTwo' },
        { text: 'Circuit 3', subtitle: 'Nom du circuit 3', icon: 'mdi-car-side', to: 'CircuitThree' },
        { text: 'Circuit Test', icon: 'mdi-bus-side', to: 'CircuitTest' },
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
