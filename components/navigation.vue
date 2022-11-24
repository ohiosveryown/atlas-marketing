<template>
  <nav>
    <div class="width wrapper">
      <nuxt-link to="/">
        <logo class="logo" />
      </nuxt-link>

      <div
        ref="menuSm"
        @click="toggleMenu(), (navOpen = !navOpen)"
        class="hamburger"
      >
        Click
      </div>

      <menu class="small dark">
        <ul>
          <li>
            <nuxt-link to="/features">Features</nuxt-link>
          </li>

          <li>
            <nuxt-link to="/pricing">Pricing</nuxt-link>
          </li>

          <li>
            <nuxt-link to="/changelog">Changelog</nuxt-link>
          </li>

          <li>
            <nuxt-link to="/about">About</nuxt-link>
          </li>

          <li>
            <a href="https://app.getatlas.io/auth/login?next=/">Log In</a>
          </li>

          <li>
            <a href="https://app.getatlas.io/auth/signup"
              ><button class="button-primary">Sign Up</button></a
            >
          </li>
        </ul>
      </menu>
      <menu class="large dark">
        <ul>
          <li>
            <nuxt-link to="/features">Features</nuxt-link>
          </li>

          <li>
            <nuxt-link to="/pricing">Pricing</nuxt-link>
          </li>

          <li>
            <nuxt-link to="/changelog">Changelog</nuxt-link>
          </li>

          <li>
            <nuxt-link to="/about">About</nuxt-link>
          </li>

          <li class="rule" />

          <li>
            <a href="https://app.getatlas.io/auth/login?next=/">Log In</a>
          </li>

          <li>
            <a href="https://app.getatlas.io/auth/signup"
              ><button class="button-primary">Sign Up</button></a
            >
          </li>
        </ul>
      </menu>
    </div>
  </nav>
</template>

<style lang="scss" scoped>
  @import "~static/style/grid.scss";

  nav {
    --spacing: 2.8rem;
    display: flex;
    position: sticky;
    z-index: var(--zmax);
    top: 0;
    height: 48px;
    font-size: 1.4rem;
    font-weight: 500;
    border-bottom: 0.5px solid rgba(255, 255, 255, 0.24);
    background: linear-gradient(#05020d, rgba(5, 2, 13, 0.4));
    backdrop-filter: blur(22px);
    transition: all 300ms ease;

    @include breakpoint(md) {
      align-items: center;
      padding: 0;
    }
  }

  .wrapper {
    display: flex;
    justify-content: space-between;
    align-items: center;
    position: relative;
  }

  .logo {
    transform: scale(0.72) translateY(0.3rem);
    transform-origin: left;
  }

  .hamburger {
    @include breakpoint(md) {
      display: none;
    }
  }

  menu.small {
    border: 0.5px solid rgba(255, 255, 255, 0.2);
    display: flex;
    position: absolute;
    top: 44px;
    width: 100%;
    padding: 1.2rem 1.8rem;
    border-radius: 12px;
    background: linear-gradient(180deg, #04020c 0%, #18043d 86%);
    box-shadow: 0px 100px 80px rgba(0, 0, 0, 0.8),
      0px 12px 10px rgba(0, 0, 0, 0.4);

    @include breakpoint(md) {
      display: none;
    }
  }

  menu.small ul {
    display: flex;
    flex-direction: column;
    width: 100%;
  }

  menu.small li {
    padding: 1.2rem 0;
    width: 100%;
    font-size: 1.8rem;
    border-bottom: 0.5px solid rgba(255, 255, 255, 0.2);

    &:last-of-type {
      border-bottom: none;
    }
  }

  menu.large {
    display: none;

    @include breakpoint(md) {
      display: flex;
    }
  }

  menu.large ul {
    @include breakpoint(md) {
      display: flex;
      align-items: center;
    }
  }

  menu.large li {
    margin-left: 2.8rem;
    transition: var(--ease);
  }

  .rule {
    position: relative;
    width: 1px;
    height: 18px;
    background: rgba(255, 255, 255, 0.56);
    pointer-events: none;
  }

  @media (pointer: fine) {
    menu.large li:hover {
      opacity: 0.72;
    }

    button:hover {
      filter: hue-rotate(20deg);
    }
  }

  button {
    background: var(--gradient-brand);
    color: #fff;
    font-size: 1.4rem;
    font-weight: 500;
    transition: filter 300ms ease;

    @include breakpoint(md) {
      // height: 3.2rem;
      padding: 0.6rem 1.6rem 0.7rem;
    }
  }

  a.nuxt-link-exact-active {
    color: #a5a5ff;
  }

  .active {
    color: red;
  }
</style>

<script>
  export default {
    data: () => ({
      navOpen: false,
    }),

    methods: {
      toggleMenu() {
        this.$refs.menuSm.classList.toggle("active")
      },
    },
  }
</script>
