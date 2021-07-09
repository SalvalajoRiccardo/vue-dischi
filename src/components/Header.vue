<template>
  <div class="barra d-flex align-items-center justify-content-between">
    <img src="https://www.cantabrialabsdifacooper.it/wp-content/uploads/2021/03/png-clipart-spotify-logo-spotify-computer-icons-podcast-music-apps-miscellaneous-angle-1-e1614848134495.png" alt="spotify">

    <Selector />
  </div>
</template>

<script>
import Selector from '@/components/Selector.vue'
export default {
  name: 'Header',
  components: {
    Selector
  }
  
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
.barra {
  width: 100%;
  height: 80px;
  background: #2e3a46;
  img {
    height: 80%;
  }
}

</style>
