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

      <section class="app-preview width">
        <HeaderMedium
          class="ente rrr"
          heading="Customer Centric Productivity"
          subheading="Build relationships with your customers by seeing them in their full context.
          See how it works below 👇"
        />

        <app-preview />
      </section>
    </main>
  </div>
</template>

<style lang="scss" scoped>
  @import "~static/style/grid.scss";

  section.hero {
    margin-bottom: 4.8rem;

    @include breakpoint(md) {
      margin-bottom: 12rem;
    }
  }

  section.features {
    @include breakpoint(md) {
      margin-bottom: 9.6rem;
    }

    header {
      margin-bottom: 2.4rem;
      text-align: center;
      @include breakpoint(md) {
        text-align: left;
        margin-bottom: 4.8rem;
        width: grid-width(5);
      }
    }
  }

  section.app-preview {
    @include breakpoint(md) {
      margin-bottom: 9.6rem;
    }

    header {
      margin-bottom: 2.4rem;
      text-align: center;
      @include breakpoint(md) {
        margin: 0 auto 4.8rem;
        width: grid-width(6.4);
      }
    }
  }
</style>

<script>
  export default {
    async asyncData({ $content, params }) {
      const features = await $content()
        .limit(6)
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

      handleScroll() {
        const observerOptions = {
          root: null,
          threshold: 0,
          rootMargin: "0px 0px -240px 0px",
        }
        const observerCallback = (entries, observer) => {
          entries.forEach((entry) => {
            if (entry.isIntersecting) {
              entry.target.classList.add("active")
            }
          })
        }
        const observer = new IntersectionObserver(
          observerCallback,
          observerOptions
        )
        const targets = document.querySelectorAll(".scroll-target")
        targets.forEach((e) => observer.observe(e))
      },
    },

    mounted() {
      this.enter(), this.handleScroll()
    },
  }
</script>
