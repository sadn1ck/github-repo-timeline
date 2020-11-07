<template>
  <div>
    <Nav />
    <Nuxt />
  </div>
</template>
<script>
import Nav from '~/components/Nav'
export default {
  components: {
    Nav,
  },
}
</script>
<style>
* {
  overflow-wrap: break-word;
}
</style>
