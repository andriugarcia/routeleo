<template>
  <article>
    <img :src="blogPost.cover">
    <div class="pa-4">
        <h1>{{blogPost.title}}</h1>
        <h2>{{blogPost.description}}</h2>
        <div v-html="$md.render(blogPost.body)" style="width: 100%"></div>
    </div>
  </article>
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
};
</script>