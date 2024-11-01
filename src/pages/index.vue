<template>
  <div>
    <main>
      <h1>Accueil</h1>
      <v-icon>mdi-star-crescent</v-icon>
      <v-icon>mdi-routes</v-icon>
      <v-icon>mdi-biathlon</v-icon>
      <v-icon><i-mdi-biathlon /></v-icon>
      <v-icon><i-fa6-brands-x-twitter /></v-icon>
      <v-icon><i-material-symbols-hiking /></v-icon>
      <v-container>
        <v-row>
          <v-col
            v-for="(card, index) in cards"
            :key="index"
            cols="12"
          >
            <v-card class="mx-auto" max-width="500">
              <v-img
                class="align-end text-white"
                cover
                height="250"
                :src="card.image"
              >
                <v-card-title>{{ card.title }}</v-card-title>
              </v-img>
              <v-card-subtitle class="pt-4">
                {{ card.subtitle }}
              </v-card-subtitle>
              <v-card-text>
                <div>{{ card.description }}</div>
              </v-card-text>
              <v-card-actions>
                <v-btn color="orange" text @click="share(card)">
                  Share
                </v-btn>
                <v-btn color="orange" text @click="explore(card)">
                  Explore
                </v-btn>
              </v-card-actions>
            </v-card>
          </v-col>
        </v-row>
      </v-container>
    </main>
  </div>
</template>

<script>
  export default {
    name: 'Index',
    data () {
      return {
        cards: [
          {
            title: 'Top 10 Australian beaches',
            subtitle: 'Number 10',
            description: 'Whitehaven Beach, Whitsunday Island, Whitsunday Islands',
            image: 'https://cdn.vuetifyjs.com/images/cards/docks.jpg',
          },
          {
            title: 'Beautiful Beach',
            subtitle: 'Number 9',
            description: 'Bondi Beach, Sydney',
            image: 'https://cdn.vuetifyjs.com/images/cards/sunshine.jpg',
          },
          {
            title: 'Amazing Beach',
            subtitle: 'Number 8',
            description: 'Manly Beach, Sydney',
            image: 'https://cdn.vuetifyjs.com/images/cards/road.jpg',
          },
          // Ajoutez d'autres cartes ici
        ],
      }
    },
  }
  </script>

<style scoped>
/* Add your styles here */
.card-border {
  border: 1px solid #ccc; /* Changez cette couleur et épaisseur selon vos besoins */
  border-radius: 8px; /* Ajoutez un rayon de bordure si nécessaire */
}
.card-background {
  background-color: white; /* Changez cette couleur selon vos besoins */
}
</style>
