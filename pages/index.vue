<template>
  <div class="app">
    <h1>Hello World</h1>

    <section class="debug width">
      <ul>
        <li v-for="feature of features" :key="feature.slug">
          <nuxt-link :to="`/features/${feature.slug}`">
            {{ feature.title }}
          </nuxt-link>
        </li>
      </ul>
    </section>
  </div>
</template>

<style lang="scss" scoped>
  @import "~static/style/grid.scss";
</style>

<script>
  export default {
    // async asyncData({ $content, params }) {
    //   const features = await $content().fetch()
    //   return { features }
    // },

    async asyncData({ $content, params }) {
      const features = await $content()
        .where({
          tags: "testing",
        })
        .fetch()

      return {
        features,
      }
    },
  }
</script>
