<template>
  <div>
    <Navbar />
    <Nuxt />
  </div>
</template>

<script>
import Navbar from '~/components/NavigationComponent.vue';

export default {
  components: {
    Navbar
  },
  name: 'DefaultLayout'
}
</script>
