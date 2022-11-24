<template>
  <header>
    <h2 class="inter fs-xl">
      {{ heading }}
    </h2>
    <h3 class="founders fs-lg dark">
      {{ subheading }}
    </h3>
  </header>
</template>

<style lang="scss" scoped>
  @import "~static/style/grid.scss";

  h2 {
    text-align: center;
    padding-bottom: 1.6rem;
    background: linear-gradient(180deg, #ffffff 0%, #d0c4e7 100%);
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;

    @include breakpoint(md) {
      text-align: left;
      padding-bottom: 2.6rem;
      line-height: 1.1;
    }
  }

  h3 {
    text-align: center;

    @include breakpoint(md) {
      text-align: left;
    }
  }
</style>

<script>
  export default {
    props: ["heading", "subheading"],
  }
</script>
