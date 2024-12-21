<template>
  <div>
    <main>
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
              />
              <v-card-title>{{ card.title }}</v-card-title>
              <v-card-text>
                <p>
                  Constantine est la capitale de l'est algérien, et parmi les plus grandes villes de l'Algérie.
                </p><br><p>
                  La vieille ville est construite sur le roche de la chaux dure, qui a donné un spectacle unique et impossible à trouver à travers le monde comme dans n'importe quelle ville.
                </p><br><p>
                  Les Français l'appelaient "le Vieux Rocher", les arabes n'ont cessé de la surnommer "Bled-el-Haoua", expression qui signifiait à la fois "Cité aérienne", "Cité du Ravin", "Cité des Passions".
                </p><br><p>
                  Pour traverser d'un côté sur l'autre côté Constantine a plusieurs ponts.
                </p>
              </v-card-text>
              <v-card-actions>
                <router-link to="Circuit">
                  <v-btn color="green" text>
                    Détails
                  </v-btn>
                </router-link>
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
          // {
          //   title: 'Circuit 1 : Patrimoine et Histoire de Constantine',
          //   subtitle: 'Durée : Environ 4 heures - Difficulté : Facile',
          //   description: 'Ce circuit vous permettra de découvrir les sites historiques les plus emblématiques de Constantine, souvent surnommée la "Ville des Ponts Suspendus".',
          //   image: 'https://upload.wikimedia.org/wikipedia/commons/thumb/9/9c/1_Pont_de_Sidi_M%27Cid.JPG/1920px-1_Pont_de_Sidi_M%27Cid.JPG',
          // },
          // {
          //   title: 'Beautiful Beach',
          //   subtitle: 'Number 9',
          //   description: 'Bondi Beach, Sydney',
          //   image: 'https://cdn.vuetifyjs.com/images/cards/sunshine.jpg',
          // },
          // {
          //   title: 'Amazing Beach',
          //   subtitle: 'Number 8',
          //   description: 'Manly Beach, Sydney',
          //   image: 'https://cdn.vuetifyjs.com/images/cards/road.jpg',
          // },
          {
            title: 'Constantine à travers ses ponts',
            subtitle: 'Number 8',
            description: 'Constantine est la capitale de l\'est algérien, et parmi les plus grandes villes de l\'Algérie. La vieille ville est construite sur le roche de la chaux dure, qui a donné un spectacle unique est impossible à trouver à travers le monde comme dans n\'importe quelle ville. Les Français l\'appelaient "le Vieux Rocher", les arabes n\'ont cessé de la surnommer "Bled-el-Haoua", expression qui signifiait à la fois "Cité aérienne", "Cité du Ravin", "Cité des Passions". Pour traverser d\'un côte sur l\'autre côté Constantine a plusieurs ponts.',
            image: new URL('@/assets/landscape2.jpg', import.meta.url).href,
          },
        // Ajoutez d'autres cartes ici
        ],
      }
    },
    methods: {
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
