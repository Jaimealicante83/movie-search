<template>
  <div class="home">
    <BuscarPeliculas />
  </div>
</template>

<script>
// @ is an alias to /src
import BuscarPeliculas from '@/components/BuscarPeliculas.vue'

export default {
  name: 'Home',
  components: {
    BuscarPeliculas
  }
}
</script>

<style scoped>
.home{
  max-width: 1300px;
  margin: 0 auto;
}
</style>
