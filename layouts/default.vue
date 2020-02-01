<template lang="pug">
  v-app(light)
    v-card.pa-3(flat)
      v-layout(align-center, justify-space-between)
        img(src="@/assets/Routeleo.png", style="height: 40px")
        v-icon mdi-menu
    v-content
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
  }
}
</script>
