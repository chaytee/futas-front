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
  .welcome-type {
    height: calc(100vh - 60px);

    @include ta {
      height: calc(100vh - 45px);
    }
  }
</style>
