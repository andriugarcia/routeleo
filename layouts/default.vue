<template lang="pug">
  v-app(light, style="background-color: #FAFAFA")
    v-layout(align-center, style="position: fixed; top: 0; left: 0; right: 0; z-index: 20", justify-space-between)
      v-flex(v-if="$vuetify.breakpoint.mdAndUp", xs12, md8)
      v-flex(xs12, md4)
        v-card.pa-3(flat, color="#FAFAFA")
          v-layout.px-4(align-center, justify-space-between)
            img(src="@/assets/Routeleo.png", style="height: 32px", @click="$router.push({path: '/'})")
            v-icon(color="green") mdi-magnify
    v-content
      v-layout(style="height: 100vh;")
        v-flex(v-if="$vuetify.breakpoint.mdAndUp", xs12, md8)
          v-img.pa-8.align-end(:src="cover", style="width: 100%; height: 100%; object-fit: cover;")
            v-layout
              v-chip.mr-3(color="white")
                v-icon mdi-airplane
              v-chip.mr-3(color="white")
                v-icon mdi-train
              v-chip.mr-3(color="white")
                v-icon mdi-bus
            h1.display-4.font-weight-bold.white--text {{ blogTitle }}
            h2.white--text Con Routeleo elige la aventura y olvidate del precio
        v-flex(xs12, md4, style="overflow-y: scroll")
          nuxt
</template>

<script>
export default {
  data () {
    return {
      clipped: false,
      drawer: false,
      fixed: false,
      items: [
        {
          icon: 'mdi-apps',
          title: 'Welcome',
          to: '/'
        },
        {
          icon: 'mdi-chart-bubble',
          title: 'Inspire',
          to: '/inspire'
        }
      ],
      miniVariant: false,
      right: true,
      rightDrawer: false,
      title: 'Vuetify.js'
    }
  },

  computed: {
    cover() {
      if (this.$route.fullPath.startsWith('/blog/')) {
        return this.$store.state.blog.cover
      }
      else {
        return "img/cover.jpg"
      }
    },

    blogTitle() {
      if (this.$route.fullPath.startsWith('/blog/')) {
        return this.$store.state.blog.title
      }
      else {
        return "El precio ya no es una excusa."
      }
    }
  }
}
</script>
