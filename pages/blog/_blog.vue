<template lang="pug">
  article
    v-img.align-end.pa-4(v-if="!$vuetify.breakpoint.mdAndUp", :src="blogPost.cover", style="width: 100%")
        h1.display-2.white--text.font-weight-bold {{blogPost.title}}
    div.pa-8.pt-12
        h2.pt-4 {{blogPost.description}}
        .markdown(v-html="$md.render(blogPost.body)")
</template>

<script>
export default {
  async asyncData({ params, payload }) {
    if (payload) return { blogPost: payload };
    else
      return {
        blogPost: await require(`~/assets/content/blog/${params.blog}.json`),
      };
  },

  mounted() {
      this.$store.commit("setBlog", this.blogPost)
  }
};
</script>
