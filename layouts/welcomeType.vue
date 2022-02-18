<template>
  <div class="wrap">
    <div id="container" class="welcome-type">
      <nuxt />
    </div>
    <Footer />
  </div>
</template>
<script>
import Footer from '../components/Footer.vue'

export default {
  components: {
    Footer,
  }
}
</script>
<style lang="scss">
  #container.welcome-type {
    height: calc(100% - 50px);
    min-height: auto;

    @include ta {
      height: calc(100% - 35px);
    }
  }
</style>
