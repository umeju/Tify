<template>
  <div>
    <h2
      class="my-3"
    >
      {{ prods.sites.operatore.denominazione }} - {{ prods.sites.operatore.citta }}
    </h2>
    <!-- {{ prods.sites.operatore.id }} - {{ prods.sites.operatore.referente }} -->
    <!-- {{ prods.sites.categorie }} -->
    <!-- <Carousel /> -->
    <div class="flexi">
      <!-- <transition-group name="list" tag="p"> -->
      <v-expansion-panels
        v-model="panel"
        multiple
        focusable
      >
        <v-expansion-panel
          v-for="(categoria, id) in prods.sites.categorie"
          :key="id"
          class="blue-grey darken-4 mt-1"
        >
          <v-expansion-panel-header
            class="mt-0 p-0 womargin"
          >
            <v-img
              class="cat-image mx-4"
              max-height="100"
              max-width="100"
              src="https://www.stepbystep.com/wp-content/uploads/2012/07/Antipasti-Platter.jpg"
            />
            {{ categoria.nome }}
          </v-expansion-panel-header>
          <v-expansion-panel-content>
            <div
              v-for="(prodotto, k) in categoria.prodotti_ingredienti_consigliati"
              :key="k"
              class="px-0"
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
                class="cat-image mt-6"
                lazy-src="https://picsum.photos/id/11/10/6"
                max-height="160"
                max-width="280"
                :src="prodotto.url_img1"
              />
              <div class="wrap-desc">
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
                  class="plus"
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
    ],
    panel: []
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
}
.descr {
  min-height: 50px;
}
.plus {
  margin: -85px 0 0 215px;
}
.womargin {
  padding: 10px !important;
}
.wrap-desc {
  margin: 0 0 -22px 0;
  max-width: 200px;
}
.text-caption {
  max-width: 277px;
  text-align: justify;
}
.cat-image {
  border-radius: 10px;
}
</style>
