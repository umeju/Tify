<template>
  <div>
    <h2
      class="my-3"
    >{{ prods.sites.operatore.denominazione }} - {{ prods.sites.operatore.citta }}
    </h2>
    <!-- {{ prods.sites.operatore.id }} - {{ prods.sites.operatore.referente }} -->
    <!-- {{ prods.sites.categorie }} -->
    <!-- <Carousel /> -->
    <div class="flexi">
      <!-- <transition-group name="list" tag="p"> -->

      <v-expansion-panels>
        <v-expansion-panel
          v-for="(categoria, id) in prods.sites.categorie"
          :key="id"
          class="blue-grey darken-4"
        >
          <v-expansion-panel-header>
            <v-img
              class="this mx-4"
              lazy-src="https://picsum.photos/id/11/10/6"
              max-height="100"
              max-width="100"
              src="https://picsum.photos/id/11/10/6"
            />
            {{ categoria.nome }}
          </v-expansion-panel-header>
          <v-expansion-panel-content>
            <div
              v-for="(prodotto, k) in categoria.prodotti_ingredienti_consigliati"
              :key="k"
              class="px-6"
            >
              <!-- <v-lazy
                v-model="isActive"
                :options="{
                  threshold: .5
                }"
                min-height="200"
                transition="fade-transition"
              > -->
              <v-img
                class="this my-0"
                lazy-src="https://picsum.photos/id/11/10/6"
                max-height="160"
                max-width="280"
                :src="prodotto.url_img1"
              />
              <div>
                <h6
                  class="mt-2"
                >
                  {{ prodotto.nome }} - € {{ prodotto.prezzo }},00
                </h6>
                <Rating />
                <v-btn
                  rounded
                  color="primary"
                  dark
                  class="butt"
                >
                  +
                </v-btn>
              </div>
              <p
                class="text-caption"
              >
                {{ prodotto.descrizione }}
              </p>
              <!-- </v-lazy> -->
            </div>
          </v-expansion-panel-content>
        </v-expansion-panel>
      </v-expansion-panels>

      <div>
        <div
          class="descr pa-2 rounded-pill"
        />
      </div>
      <!-- </transition-group> -->
    </div>
    <Footer />
  </div>
</template>
<script>
export default {
  props: {
    affessa: {
      type: String,
      default: ''
    }
  },
  async asyncData ({ $axios, $config }) {
    const prods = await $axios.$get('/gmapi/23/1')
    return { prods }
  },
  data: () => ({
    rating: 4,
    isActive: false,
    icons: [
      'mdi-facebook',
      'mdi-twitter',
      'mdi-linkedin',
      'mdi-instagram'
    ]
  })
}
</script>

<style>
.flexi {
  display: flex;
  flex-direction: row;
  flex-wrap: wrap;
  background-color: rgb(167, 163, 172);
  justify-content: center;
}
.flexi div {
  flex-direction: row;
  /* margin: 10px; */
  content: "";
  margin: 0px;
}
.descr {
  min-height: 50px;
}
.butt {
  height: 36px;
  min-width: 64px;
  padding: 0 16px;
  top: -30px;
  left: 215px;
}
</style>
