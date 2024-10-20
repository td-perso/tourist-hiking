<template>
  <div>
    <v-navigation-drawer v-model="drawer" app>
      <v-list flat>
        <v-subheader>MENU</v-subheader>
        <v-list-item-group v-model="selectedItem" color="primary">
          <v-list-item v-for="(item, i) in items" :key="i" link :to="item.to">
            <v-list-item-icon>
              <v-icon>{{ item.icon }}</v-icon>
            </v-list-item-icon>
            <v-list-item-content>
              <v-list-item-title>{{ item.text }}</v-list-item-title>
            </v-list-item-content>
          </v-list-item>
        </v-list-item-group>
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
        { text: 'Home', icon: 'mdi-home', to: 'Index' },
        { text: 'Page1', icon: 'mdi-arrow-right-box', to: 'PageOne' },
        { text: 'Page2', icon: 'mdi-arrow-right-box', to: 'PageTwo' },
        { text: 'Page3', icon: 'mdi-arrow-right-box', to: 'PageThree' },
        { text: 'AppPinia', icon: 'mdi-arrow-right-box', to: 'appPinia' },
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
