<template>
  <article>
    <h1>{{blogPost.title}}</h1>
    <h2>{{blogPost.description}}</h2>
    <div v-html="$md.render(blogPost.body)"></div>
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