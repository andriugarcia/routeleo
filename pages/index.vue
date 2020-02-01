<template lang="pug">
  h1 Hola mundo
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
