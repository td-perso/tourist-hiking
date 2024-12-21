<template>
  <v-dialog v-model="dialog" max-width="600px">
    <v-card>
      <template #append>
        <v-btn
          icon="$close"
          size="large"
          variant="text"
          @click="closeDialog"
        />
      </template>
      <v-card-text class="d-flex justify-center">
        <v-img contain max-height="80vh" :src="img" width="100%" />
      </v-card-text>
    </v-card>
  </v-dialog>
  <v-container>
    <v-row dense>
      <v-col cols="12">
        <h1>Constantine à travers ses ponts</h1>
      </v-col>
    </v-row>
    <v-row dense>
      <v-col cols="12">
        <v-carousel>
          <v-carousel-item
            v-for="(card, index) in cards"
            :key="index"
            cover
            :src="card.image"
          />
        </v-carousel>
      </v-col>
    </v-row>
    <v-row dense>
      <v-col cols="12">
        <iframe
          allowfullscreen
          frameborder="0"
          height="500"
          src="https://www.google.com/maps/d/embed?mid=1Co0mKwblYiWfbp14ll5Z4R_6wMiAwx8&ehbc=2E312F&noprof=1"
          style="border:none;"
          width="100%"
        />
      </v-col>
    </v-row>
    <v-row dense>
      <v-col cols="12">
        <v-card>
          <v-card-title class="text-h5">
            Introduction
          </v-card-title>
          <v-card-text class="py-0">
            <v-row align="start" no-gutters>
              <v-col
                cols="6"
              >
                <p>
                  Constantine est la capitale de l'est algérien, et parmi les plus grandes villes de l'Algérie.
                </p><br><p>
                  La vieille ville est construite sur le roche de la chaux dure, qui a donné un spectacle unique et impossible à trouver à travers le monde comme dans n'importe quelle ville.
                </p><br><p>
                  Les Français l'appelaient "le Vieux Rocher", les arabes n'ont cessé de la surnommer "Bled-el-Haoua", expression qui signifiait à la fois "Cité aérienne", "Cité du Ravin", "Cité des Passions".
                </p><br><p>
                  Pour traverser d'un côté sur l'autre côté Constantine a plusieurs ponts.
                </p>
              </v-col>
              <v-col cols="6">
                <v-img
                  class="pointer"
                  height="250"
                  src="@/assets/acces.png"
                  @click="openDialog('acces')"
                />
              </v-col>
            </v-row>
          </v-card-text>
        </v-card>
      </v-col>
    </v-row>
    <v-row dense>
      <v-col cols="12">
        <v-card>
          <v-card-title class="text-h5">
            Le circuit
          </v-card-title>
          <v-card-text class="py-0">
            <v-row align="start" no-gutters>
              <v-col
                cols="6"
              >
                <p>
                  <v-icon><i-material-symbols-light-award-star-outline /></v-icon>
                  Distance : <span style="color: #8B0A1A">2.73 Km</span>
                </p><p>
                  <v-icon><i-material-symbols-light-award-star-outline /></v-icon>
                  Situation : <span style="color: #8B0A1A">La vielle ville de Constantine</span>
                </p><p>
                  <v-icon><i-material-symbols-light-award-star-outline /></v-icon>
                  Mode de déplacement : <span style="color: #8B0A1A">A pied pour un circuit long et le téléphérique pour un circuit court</span>
                </p><p>
                  <v-icon><i-material-symbols-light-award-star-outline /></v-icon>
                  Durée : <span style="color: #8B0A1A">1h à pied</span> et <span style="color: #8B0A1A">3 minutes pour le téléphérique</span>
                </p>
                <p>
                  <v-icon><i-material-symbols-light-award-star-outline /></v-icon>
                  Les huit ponts de la ville de Constantine :
                </p>
                <ul style="margin-left: 4em">
                  <li>Le pont Suspendu</li><li>Le pont des chutes</li><li>Le pont El Kantra</li><li>La passerelle Perrégaux</li><li>Le pont Sidi Rached</li><li>Le pont du diable</li><li>Le pont Medjaz Laghnem</li><li>Le pont Saleh Bey</li>
                </ul>
              </v-col>
              <v-col cols="6">
                <a class="access-link" href="#" @click.prevent="openDialog('circuit')">
                  <v-img height="250" src="@/assets/circuit.jpg" @click="openDialog('circuit')" />
                </a>
              </v-col>
            </v-row>
          </v-card-text>
        </v-card>
      </v-col>
    </v-row>
    <v-row dense>
      <v-col cols="12">
        <v-card>
          <v-card-title class="text-h5">
            1 - Pont Suspendu
          </v-card-title>

          <v-card-text>
            <v-row align="center">
              <v-col
                cols="2"
              >
                <v-img height="100" src="@/assets/1-1.jpg" />
              </v-col>
              <v-col
                cols="10"
              >
                <p>
                  <v-icon><i-material-symbols-light-award-star-outline /></v-icon>
                  Le pont Suspendu, ou passerelle de Sidi M'Cid, traverse les gorges à <span style="color: #8B0A1A">17 mètres</span> au-dessus du Rhumel. Cet ouvrage est <span style="color: #8B0A1A">long de 164 mètres</span>, large de <span style="color: #8B0A1A">5,70 mètres</span> et supporte une charge de <span style="color: #8B0A1A">17 tonnes</span>.
                </p>
              </v-col>
            </v-row>
            <v-row align="center">
              <v-col
                cols="10"
              >
                <p>
                  <v-icon><i-material-symbols-light-award-star-outline /></v-icon>
                  Conçu par l'ingénieur Ferdinand Arnodin, il a été réalisé par <span style="color: #8B0A1A">l'entreprise Witte</span>.
                </p><br><p>
                  <v-icon><i-material-symbols-light-award-star-outline /></v-icon>
                  Son inauguration eu lieu le <span style="color: #8B0A1A">19 avril 1912</span>.
                </p>
              </v-col>
              <v-col
                cols="2"
              >
                <v-img height="100" src="@/assets/1-2.jpg" />
              </v-col>
            </v-row>
          </v-card-text>
        </v-card>
      </v-col>
    </v-row>
    <v-row dense>
      <v-col cols="12">
        <v-card>
          <v-card-title class="text-h5">
            2 - Pont des chutes
          </v-card-title>
          <v-card-text>
            <v-row align="center">
              <v-col
                cols="2"
              >
                <v-img height="100" src="@/assets/2-1.jpg" />
              </v-col>
              <v-col
                cols="10"
              >
                <p>
                  <v-icon><i-material-symbols-light-award-star-outline /></v-icon>
                  Le pont des <span style="color: #8B0A1A">chutes</span>, Construit <span style="color: #8B0A1A">en 1925</span> , il franchi le Rhumel juste à la sortie des gorges, presque sous la passerelle de Sidi M'Cid.
                </p>
              </v-col>
            </v-row>
            <v-row align="center">
              <v-col
                cols="10"
              >
                <p><v-icon><i-material-symbols-light-award-star-outline /></v-icon>Les eaux de l'oued se précipitent alors, en plusieurs chutes, d'une hauteur de <span style="color: #8B0A1A">80 mètres</span> vers la plaine du Hamma.</p>
              </v-col>
              <v-col
                cols="2"
              >
                <v-img height="100" src="@/assets/2-2.jpg" />
              </v-col>
            </v-row>
            <v-row align="center">
              <v-col
                cols="2"
              >
                <v-img height="100" src="@/assets/2-3.jpg" />
              </v-col>
              <v-col
                cols="10"
              >
                <p><v-icon><i-material-symbols-light-award-star-outline /></v-icon>A cet endroit les gorges dominent d'une hauteur de <span style="color: #8B0A1A">200 mètres</span>. En arrière plan du pont se développe l'arche naturelle au dessus de l'oued Rhumel.</p>
              </v-col>
            </v-row>
          </v-card-text>
        </v-card>
      </v-col>
    </v-row>
    <v-row dense>
      <v-col cols="12">
        <v-card>
          <v-card-title class="text-h5">
            3 - Pont El Kantra
          </v-card-title>
          <v-card-text>
            <v-row align="center">
              <v-col
                cols="10"
              >
                <p><v-icon><i-material-symbols-light-award-star-outline /></v-icon>Le pont <span style="color: #8B0A1A">d’El Kantara</span> fut construit par <span style="color: #8B0A1A">Salah Bey en 1792</span> sur les ruines d’un ancien pont romain.</p>
              </v-col>
              <v-col
                cols="2"
              >
                <v-img height="100" src="@/assets/3-1.jpg" />
              </v-col>
            </v-row>
            <v-row align="center">
              <v-col
                cols="2"
              >
                <v-img height="100" src="@/assets/3-2.jpg" />
              </v-col>
              <v-col
                cols="10"
              >
                <p><v-icon><i-material-symbols-light-award-star-outline /></v-icon>En <span style="color: #8B0A1A">1836</span>,lors de la première expédition contre la ville, les troupes du général Trezel tentent de faire sauter la porte qui ferme le pont.</p>
              </v-col>
            </v-row>
            <v-row align="center">
              <v-col
                cols="10"
              >
                <p><v-icon><i-material-symbols-light-award-star-outline /></v-icon><span style="color: #8B0A1A">Le 18 mars 1857</span>, le pont s'effondre après le passage d'un détachement d'infanterie.</p>

                <p><v-icon><i-material-symbols-light-award-star-outline /></v-icon>Après <span style="color: #8B0A1A">trois ans de travaux</span>, l'ouvrage actuel est ouvert <span style="color: #8B0A1A">en 1863</span>.</p>
              </v-col>
              <v-col
                cols="2"
              >
                <v-img height="100" src="@/assets/3-3.jpg" />
              </v-col>
            </v-row>
            <v-row align="center">
              <v-col
                cols="2"
              >
                <v-img height="100" src="@/assets/3-4.jpg" />
              </v-col>
              <v-col
                cols="10"
              >
                <p><v-icon><i-material-symbols-light-award-star-outline /></v-icon>Le pont d'El Kantara mesure <span style="color: #8B0A1A">128 mètres</span> de long et domine le Rhumel d'une hauteur de <span style="color: #8B0A1A">125 mètres</span>.</p>
              </v-col>
            </v-row>
          </v-card-text>
        </v-card>
      </v-col>
    </v-row>
    <v-row dense>
      <v-col cols="12">
        <v-card>
          <v-card-title class="text-h5">
            4 - Passerelle Perrégaux
          </v-card-title>

          <v-card-text>
            <v-row align="center">
              <v-col
                cols="2"
              >
                <v-img height="100" src="@/assets/4-1.jpg" />
              </v-col>
              <v-col
                cols="10"
              >
                <p><v-icon><i-material-symbols-light-award-star-outline /></v-icon>Cette passerelle illustre la technique des ponts suspendus et peut être considérée comme le modèle réduit du pont Sidi Mcid.</p>

                <p><v-icon><i-material-symbols-light-award-star-outline /></v-icon>Construite entre <span style="color: #8B0A1A">1917 et 1925</span>, elle fut ouverte à la circulation le <span style="color: #8B0A1A">12 avril de la même année</span>, elle est réservée aux piétons, et <span style="color: #8B0A1A">mesure 125 mètres de long</span>, pour une <span style="color: #8B0A1A">largeur de 2,40 mètres</span>.</p>
              </v-col>
            </v-row>
            <v-row align="center">
              <v-col
                cols="10"
              >
                <p><v-icon><i-material-symbols-light-award-star-outline /></v-icon>La passerelle Perrégaux ( aujourd'hui Mellah Slimane) ou pont de l'ascenseur, relie le quartier de la gare au centre-ville, via un escalier, ou l'ascenseur de la Merdersa.</p>
              </v-col>
              <v-col
                cols="2"
              >
                <v-img height="100" src="@/assets/4-2.jpg" />
              </v-col>
            </v-row>
          </v-card-text>
        </v-card>
      </v-col>
    </v-row>
    <v-row dense>
      <v-col cols="12">
        <v-card>
          <v-card-title class="text-h5">
            5 - Pont Sidi Rached
          </v-card-title>

          <v-card-text>
            <v-row align="center">
              <v-col
                cols="2"
              >
                <v-img height="100" src="@/assets/5-1.jpg" />
              </v-col>
              <v-col
                cols="10"
              >
                <p><v-icon><i-material-symbols-light-award-star-outline /></v-icon>La construction du pont de Sidi Rached est lancé en <span style="color: #8B0A1A">1907</span>, le projet est confié à <span style="color: #8B0A1A">M. Georges Boisnier</span> spécialiste des grands ponts.</p>
              </v-col>
            </v-row>
            <v-row align="center">
              <v-col
                cols="10"
              >
                <p><v-icon><i-material-symbols-light-award-star-outline /></v-icon>Réalisé en <span style="color: #8B0A1A">pierres de taille</span>, ce pont en trois courbes, est long de <span style="color: #8B0A1A">447 mètres</span>. il repose sur 27 arches dont 13ont une ouverture de 8,80 mètres, une de <span style="color: #8B0A1A">30 mètres</span> et la plus large de <span style="color: #8B0A1A">70 mètres</span> franchit le Rhumel à <span style="color: #8B0A1A">105 mètres</span> de hauteur.</p>
              </v-col>
              <v-col
                cols="2"
              >
                <v-img height="100" src="@/assets/5-2.jpg" />
              </v-col>
            </v-row>
            <v-row align="center">
              <v-col
                cols="2"
              >
                <v-img height="100" src="@/assets/5-3.jpg" />
              </v-col>
              <v-col
                cols="10"
              >
                <p><v-icon><i-material-symbols-light-award-star-outline /></v-icon>Sa largeur est de <span style="color: #8B0A1A">12 mètres</span>. Il est, lors de sa construction, <span style="color: #8B0A1A">le plus haut pont de pierre du monde</span>.</p>
              </v-col>
            </v-row>
            <v-row align="center">
              <v-col
                cols="10"
              >
                <p><v-icon><i-material-symbols-light-award-star-outline /></v-icon>Le pont de Sidi Rached est inauguré <span style="color: #8B0A1A">le 19 avril 1912</span>.</p>
              </v-col>
              <v-col
                cols="2"
              >
                <v-img height="100" src="@/assets/5-4.gif" />
              </v-col>
            </v-row>
          </v-card-text>
        </v-card>
      </v-col>
    </v-row>
    <v-row dense>
      <v-col cols="12">
        <v-card>
          <v-card-title class="text-h5">
            6 - Pont du Diable
          </v-card-title>

          <v-card-text>
            <v-row align="center">
              <v-col
                cols="2"
              >
                <v-img height="100" src="@/assets/6-1.jpg" />
              </v-col>
              <v-col
                cols="10"
              >
                <p><v-icon><i-material-symbols-light-award-star-outline /></v-icon>Le pont <span style="color: #8B0A1A">du Diable</span> a été Construit au départ <span style="color: #8B0A1A">par les turcs</span> au pied du "Rocher des Martyrs".</p>
                <p><v-icon><i-material-symbols-light-award-star-outline /></v-icon>Il semble que son nom vienne du bruit Infernal des eaux tumultueuses qui pénètrent dans les gorges à cet endroit.</p>
              </v-col>
            </v-row>
            <v-row align="center">
              <v-col
                cols="10"
              >
                <p><v-icon><i-material-symbols-light-award-star-outline /></v-icon>Le pont du Diable se situe presque à l'aplomb du Pont Sidi Rached.</p>

                <p><v-icon><i-material-symbols-light-award-star-outline /></v-icon>C'est de ce pont que l'on accède au "Chemins des Touristes", promenade qui parcourt Les gorges sur toute leur longueur pour déboucher près du pont des chutes.</p>
              </v-col>
              <v-col
                cols="2"
              >
                <v-img height="100" src="@/assets/6-2.jpg" />
              </v-col>
            </v-row>
          </v-card-text>
        </v-card>
      </v-col>
    </v-row>
    <v-row dense>
      <v-col cols="12">
        <v-card>
          <v-card-title class="text-h5">
            7 - Pont Djez el Guenem
          </v-card-title>

          <v-card-text>
            <v-row align="center">
              <v-col
                cols="12"
              >
                <p><v-icon><i-material-symbols-light-award-star-outline /></v-icon>Ou le pont <span style="color: #8B0A1A">d’Arcole, pont métallique</span> reliant entre eux les quartiers de la basse ville.</p>
              </v-col>
            </v-row>
          </v-card-text>
        </v-card>
      </v-col>
    </v-row>
    <v-row dense>
      <v-col cols="12">
        <v-card>
          <v-card-title id="title8" class="text-h5">
            8 - Pont Saleh Bey
          </v-card-title>

          <v-card-text>
            <v-row align="center">
              <v-col
                cols="2"
              >
                <v-img height="100" src="@/assets/8-1.png" />
              </v-col>
              <v-col
                cols="10"
              >
                <p><v-icon><i-material-symbols-light-award-star-outline /></v-icon>C'est le huitième pont que compte la ville de Constantine.</p>

                <p><v-icon><i-material-symbols-light-award-star-outline /></v-icon>Il a été confié en étude et réalisation au groupement <span style="color: #8B0A1A">brésilien Andrade-Gutierrez</span>, les lancements des travaux ont eu lieu en <span style="color: #8B0A1A">2010</span>.</p>

                <p><v-icon><i-material-symbols-light-award-star-outline /></v-icon>Le viaduc a été mis en service <span style="color: #8B0A1A">le 26 juillet 2014</span>.</p>
              </v-col>
            </v-row>
            <v-row align="center">
              <v-col
                cols="10"
              >
                <p><v-icon><i-material-symbols-light-award-star-outline /></v-icon>Le pont est d'une <span style="color: #8B0A1A">largeur de 27,34m</span> pour <span style="color: #8B0A1A">2 x 2 voies</span>, en plus de trottoirs pour la sécurité des  piétons, relie sur une distance de plus de <span style="color: #8B0A1A">1100m</span>, après avoir enjambé le lit du Rhummel qui se trouve plus de <span style="color: #8B0A1A">130m</span> plus bas.</p>

                <p><v-icon><i-material-symbols-light-award-star-outline /></v-icon>A noter que le viaduc sera relié à l'autoroute Est-Ouest.</p>
              </v-col>
              <v-col
                cols="2"
              >
                <v-img height="100" src="@/assets/8-2.jpg" />
              </v-col>
            </v-row>
          </v-card-text>
        </v-card>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
  import { useGoTo } from 'vuetify'

  export default {
    name: 'Circuit',
    setup () {
      const goTo = useGoTo()
      return { goTo }
    },
    data () {
      return {
        dialog: false,
        imgPath: '',
        imgUrl: '',
        imgAcces: new URL('@/assets/acces.png', import.meta.url).href,
        imgCircuit: new URL('@/assets/circuit.jpg', import.meta.url).href,
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
      openDialog (img) {
        switch (img) {
          case 'circuit': this.img = new URL('@/assets/circuit.jpg', import.meta.url).href; break
          case 'acces': this.img = new URL('@/assets/acces.png', import.meta.url).href; break
        }
        this.dialog = true
      },
      closeDialog () { this.dialog = false },
      onClick (title) {
        this.goTo(title)
      },
    },
  }
</script>

<style scoped>
  h1 {
    color: white;
    text-align: center;
  }
  .pointer {
  cursor: pointer;
}
</style>
