<template lang="pug">
    #Blogs.px-2.mt-12.pt-6
        v-card.mb-2(v-for="(blog, i) in blogPosts", :key="i", style="border-radius: 12px", @click="$router.push({path: `/blog/${blog.slug}`})")
            img(:src="blog.cover", style="width: 100%; height: 100px; object-fit: cover")
            .pa-2
                v-layout(justify-space-between, align-center)
                    b {{ blog.title }}
                    v-chip(label, color="grey lighten-3")
                        i {{ blog.date | toDate }}
                p {{ blog.description }}

</template>

<script>
export default {
    computed: {
        blogPosts() {
            console.log(this.$store.state.blogPosts)
            return this.$store.state.blogPosts;
        },
    },

    filters: {
        toDate(value) {
            let date = new Date(value)
            return `${date.getDate()}/${date.getMonth() + 1}/${date.getFullYear()}`
        }
    }
}
</script>