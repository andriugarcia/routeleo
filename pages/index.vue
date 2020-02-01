<template lang="pug">
  #index
    v-layout
      v-flex(v-if="$vuetify.breakpoint.mdAndUp", xs12, md8)
        img(src="/img/cover.jpg", style="width: 100%; height: 100%; object-fit: cover;")
      v-flex.px-4(xs12, md4)
        v-card.pa-3(style="border-radius: 24px")
          v-text-field(solo, flat, placeholder="Origen", style="font-size: 1.2em")
          v-divider
          v-text-field(solo, flat, placeholder="Destino", style="font-size: 1.2em")
          v-layout.px-4(justify-space-between)
            .grey--text(style="font-size: 1.2em") 16 Fec
            v-divider(vertical)
            .grey--text(style="font-size: 1.2em") Añadir vuelta
          v-btn.mt-4.font-weight-bold(rounded, block, dark, color="teal lighten-2") Busca el mejor precio
        v-layout.mt-6(justify-space-between, align-center)
          b Los más buscados
          v-btn.text--overline(text, small) VER MAS
        v-layout.mt-4.hide-overflow
          div.pa-4.mr-2(v-for="i in 6", :key="i", style="background-image: url('/img/madrid.jpg'); border-radius: 16px; min-width: 160px")
            div.font-weight-bold.white--text(style="font-size: 1.6em; margin-top: 140px") Madrid
            div.font-weight-bold.white--text(style="font-size: 1.2em") Desde <b>48€</b>
        b.mt-12 Selección de Routeleo
    

</template>

<script>

export default {
  head() {
    return {
      script: [{ src: 'https://identity.netlify.com/v1/netlify-identity-widget.js' }],
    };
  },

  components: {
  }
}
</script>
