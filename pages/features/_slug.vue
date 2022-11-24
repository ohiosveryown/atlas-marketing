<template>
  <div>
    <div>
      <nuxt-link to="/">Back to blog</nuxt-link>
    </div>
    <hr />
    <div v-if="feature">
      <h1>{{ feature.title }}</h1>
      <nuxt-content :document="feature" />
    </div>
  </div>
</template>

<script>
  export default {
    async asyncData({ $content, params }) {
      const slug = params.slug
      const feature = await $content(slug).fetch()
      return { feature }
    },

    head() {
      return {
        title: `${this.feature.title} | Atlas`,
        meta: [
          {
            hid: "description",
            name: "description",
            content: this.feature.description,
          },
        ],
      }
    },
  }
</script>
