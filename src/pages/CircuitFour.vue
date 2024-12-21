<template>
  <div>
    <h1>Constantine à travers ses ponts</h1>
    <iframe
      allowfullscreen
      frameborder="0"
      height="500"
      src="https://maps.openrouteservice.org/#/directions/%D8%AC%D8%B3%D8%B1%20%D8%B3%D9%8A%D8%AF%D9%8A%20%D9%85%D8%B3%D9%8A%D8%AF,CO,Algeria/%D8%AC%D8%B3%D8%B1%20%D8%A7%D9%84%D8%B4%D9%84%D8%A7%D9%84%D8%A7%D8%AA,CO,Algeria/%D8%AC%D8%B3%D8%B1%20%D8%A8%D8%A7%D8%A8%20%D8%A7%D9%84%D9%82%D9%86%D8%B7%D8%B1%D8%A9,CO,Algeria/Passerelle%20Slimane%20Mellah,CO,Algeria/Sayyidi%20Rashid%20Bridge,CO,Algeria/Sayyidi%20Rashid%20Bridge,CO,Algeria/%D8%AC%D8%B3%D8%B1%20%D8%B5%D8%A7%D9%84%D8%AD%20%D8%A8%D8%A7%D9%8A,CO,Algeria/Pont%20Salah%20Bey,CO,Algeria/data/55,130,32,198,15,97,4,224,38,9,96,59,2,24,5,192,166,6,113,0,184,64,54,0,233,240,17,128,22,0,152,0,227,32,86,19,104,25,138,128,24,175,192,26,70,140,96,118,11,104,183,203,215,149,18,165,120,6,226,42,68,133,22,77,24,4,227,40,196,175,124,100,184,247,228,185,175,54,140,201,149,232,218,113,117,74,152,141,50,81,133,123,219,11,114,80,174,96,238,228,164,200,97,82,197,50,18,18,86,85,39,110,124,121,22,123,85,42,70,22,18,115,82,53,1,86,18,54,77,10,94,48,136,252,123,72,134,52,132,159,123,37,121,37,16,166,90,108,245,42,114,138,0,171,26,50,68,241,56,134,110,90,124,22,5,43,48,218,74,1,10,21,46,178,33,22,227,59,10,82,64,198,90,94,42,238,103,57,190,22,85,40,204,234,16,14,16,8,0,7,84,120,8,68,108,28,80,0,47,40,0,91,92,6,109,221,232,8,0,51,120,0,27,116,92,16,71,168,84,0,90,0,119,100,11,192,13,100,128,3,153,108,64,247,116,35,221,13,7,66,32,192,239,60,28,50,9,116,187,195,96,232,88,8,0,11,227,138,0,0/embed/fr-fr"
      style="border:none"
      width="100%"
    />
    <v-container>
      <v-row dense>
        <v-col v-for="(card, index) in cards" :key="index" cols="12">
          <v-card :color="card.color">
            <div class="d-flex flex-no-wrap justify-space-between">
              <div>
                <v-card-title class="text-h5">
                  {{ card.title }}
                </v-card-title>

                <v-card-subtitle>
                  {{ card.subtitle }}
                </v-card-subtitle>

                <v-card-actions>
                  <v-btn v-if="card.button" :text="card.button.text" :variant="card.button.variant" />
                  <v-btn v-if="card.icon" :icon="card.icon" :variant="card.iconVariant" />
                </v-card-actions>
              </div>

              <v-avatar class="ma-3" rounded="0" size="125">
                <v-img :src="card.image" />
              </v-avatar>
            </div>
          </v-card>
        </v-col>
      </v-row>
    </v-container>
  </div>
</template>

<script>
  export default {
    name: 'Circuit',
    data () {
      return {
        cards: [
          {
            image: new URL('@/assets/landscape1.jpg', import.meta.url).href,
            title: 'Pont Suspendu',
            subtitle: 'subtitle',
          },
          {
            image: new URL('@/assets/landscape2.jpg', import.meta.url).href,
            title: 'title',
            subtitle: 'subtitle',
          },
          {
            image: new URL('@/assets/landscape3.jpg', import.meta.url).href,
            title: 'title',
            subtitle: 'subtitle',
          },
          {
            image: new URL('@/assets/landscape4.jpg', import.meta.url).href,
            title: 'title',
            subtitle: 'subtitle',
          },
          {
            image: new URL('@/assets/landscape5.jpg', import.meta.url).href,
            title: 'title',
            subtitle: 'subtitle',
          },
          {
            image: new URL('@/assets/landscape6.jpg', import.meta.url).href,
            title: 'title',
            subtitle: 'subtitle',
          },
          {
            image: new URL('@/assets/landscape7.jpg', import.meta.url).href,
            title: 'title',
            subtitle: 'subtitle',
          },
          {
            image: new URL('@/assets/landscape8.jpg', import.meta.url).href,
            title: 'title',
            subtitle: 'subtitle',
          },
        ],
      }
    },
    methods: {
    },
  }
</script>

<style scoped>
  h1 {
    color: white;
    text-align: center;
  }
</style>
