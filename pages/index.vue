<template lang="pug">
  #index.pa-4.pt-12
    v-card.mt-3.pa-3(style="border-radius: 24px")
      v-autocomplete(v-model="idaSearch", :items="cities", hide-details, color="green", solo, flat, placeholder="Origen", style="font-size: 1.2em")
      v-layout(align-center)
        v-divider
        v-btn.ml-2(text, small, @click="invertCities")
          v-icon(color="grey darken-2") mdi-swap-vertical
      v-autocomplete(v-model="vueltaSearch", :items="cities", hide-details, color="green", solo, flat, placeholder="Destino", style="font-size: 1.2em")
      v-layout.px-4.mt-3(justify-space-between)
        v-menu(v-model="menuida", offset-y)
          template(v-slot:activator="{ on }")
            .grey--text(style="font-size: 1.2em", v-on="on") {{ idaComputed }}
          v-date-picker(v-model="ida", color="teal", no-title, scrollable, @input="menuida = false", locale="es")
        v-divider(vertical)
        v-menu(v-model="menuvuelta", offset-y)
          template(v-slot:activator="{ on }")
            .grey--text(style="font-size: 1.2em", v-on="on") {{ vueltaComputed }}
          v-date-picker(v-model="vuelta", color="teal", no-title, scrollable, :allowed-dates="allowedDates", @input="menuvuelta = false", locale="es")
            v-btn(outlined, color="red", @click="vuelta = null", block) Quitar vuelta
      v-btn.mt-4.font-weight-bold(rounded, block, dark, color="teal") Busca el mejor precio
    v-layout.mt-6(justify-space-between, align-center)
      b Los más buscados
      v-btn.text--overline(text, small) VER MAS
    v-layout.my-4.hide-overflow
      v-img.pa-2.mr-2(v-for="i in 6", :key="i", :src="require('~/static/img/madrid.jpg')", style="width: 150px; border-radius: 16px", gradient="to top right, rgba(100,115,201,.33), rgba(25,32,72,.7)")
        div.font-weight-bold.white--text(style="font-size: 1.6em; margin-top: 140px") Madrid
        div.font-weight-bold.white--text(style="font-size: 1.2em") Desde <b>48€</b>
    b.mb-2 Selección de Routeleo
    v-card.mt-2(v-for="i in 6", :key="i", style="border-radius: 16px;")
      v-img.align-end(:src="require('~/static/img/madrid.jpg')", gradient="to top right, rgba(100,115,201,.33), rgba(25,32,72,.7)")
        v-card-title.white--text.font-weight-bold Madrid
      v-layout.pa-4(justify-space-between, align-center)
        b 23 dic - 5 ene
        v-chip.font-weight-bold.white--text(color="teal") 30€

    

</template>

<script>
import moment from 'moment'

export default {
  data() {
    return {
      idaSearch: "",
      vueltaSearch: "",
      cities: ["Granada", "Madrid", "Varsovia"],
      ida: new Date().toISOString().substr(0, 10),
      vuelta: null,
      menuida: false,
      menuvuelta: false
    }
  },

methods: {
  allowedDates (val) {return new Date(val) >= new Date(this.ida)},
  invertCities() {
    let aux = this.idaSearch
    this.idaSearch = this.vueltaSearch
    this.vueltaSearch = aux
  }
},

computed: {
      idaComputed () {
        return this.ida ? moment(this.ida).format('DD/MM/YYYY') : ''
      },
      vueltaComputed () {
        return this.vuelta ? moment(this.vuelta).format('DD/MM/YYYY') : 'Añadir vuelta'
      },
    },

  head() {
    return {
      script: [{ src: 'https://identity.netlify.com/v1/netlify-identity-widget.js' }],
    };
  },

  components: {
  }
}
</script>
