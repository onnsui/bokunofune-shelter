<template>
  <section class="slug">
    <h1 class="slug_title">{{ post.fields.title }}</h1>
    <p class="slug_date">
      {{ (new Date(post.fields.publishedAt)).toLocaleDateString() }}
    </p>
    <img
      :src="post.fields.headerImage.fields.file.url"
      class="slug_image">
    {{ post.fields.body }}
  </section>
</template>

<script>
// import VueMarkdown from 'vue-markdown'
import { createClient } from '~/plugins/contentful.js'

const client = createClient()
export default {
  transition: 'slide-left',
  // components: {
  //   VueMarkdown,
  // },
  async asyncData({ env, params }) {
    return await client
      .getEntries({
        content_type: env.CTF_BLOG_POST_TYPE_ID,
        'fields.slug': params.slug,
        order: '-sys.createdAt',
      })
      .then(entries => {
        return {
          post: entries.items[0],
        }
      })
      .catch(console.error)
  },
}
</script>

<style scoped>
.slug {
  max-width: 800px;
  margin: 0 auto;
}
.slug_title {
  font-size: 2rem;
  font-weight: bolder;
}
.slug_date {
  font-size: 1rem;
  color: rgb(57, 72, 85);
  text-align: right;
}
</style>
