<template>
  <div class="app">
    <HeaderLarge
      class="width"
      heading="Give your customers superhuman support"
      subheading="Atlas is a blazingly fast, modern support platform, helping identify and diagnose customer experience and interaction."
    />

    <main class="skew-enter">
      <section class="hero width">
        <figure>
          <img
            src="https://res.cloudinary.com/da32ufmnf/image/upload/v1668962888/atlas-refresh/index/cmk7xbfccjnfmyyr2lok.png"
            alt="Atlas Customer Timeline"
          />
        </figure>
      </section>

      <section class="features width">
        <HeaderMedium
          class="enter"
          heading="A fully integrated suite of support products"
          subheading="All of the best-in-class support tools, built specifically for support teams."
        />

        <ul class="feature-grid">
          <li
            class="card card-lg"
            v-for="feature of features"
            :key="feature.slug"
          >
            <nuxt-link :to="`/features/${feature.slug}`">
              <i>{{ feature.icon }}</i>

              <h3 class="inter">
                {{ feature.title }}
              </h3>

              <p class="dark">{{ feature.description }}</p>

              <img :src="`${feature.hero}`" />
            </nuxt-link>
          </li>
        </ul>
      </section>
    </main>
  </div>
</template>

<style lang="scss" scoped>
  @import "~static/style/grid.scss";

  section.hero {
    margin-bottom: 4.8rem;

    @include breakpoint(md) {
      margin-bottom: 17.6rem;
    }
  }

  section.features {
    header {
      @include breakpoint(md) {
        width: grid-width(5);
      }
    }
  }
</style>

<script>
  export default {
    async asyncData({ $content, params }) {
      const features = await $content()
        .limit(7)
        .where({
          tags: "testing",
        })
        .fetch()

      return {
        features,
      }
    },

    methods: {
      enter() {
        gsap.from(".skew-enter", {
          opacity: 0,
          duration: 1.2,
          delay: 0.15,
          stagger: 0.15,
          skewY: 10,
          y: 120,
          ease: Power4.easeOut,
        })
      },
    },

    mounted() {
      this.enter()
    },
  }
</script>
