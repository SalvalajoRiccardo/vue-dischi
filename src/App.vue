<template>
  <div id="app">
    <div class="row">
      <div class="col-lg-12">
        <Header />
      </div>
      
      <main>
        <DiskList />
      </main>
    </div>
  </div>
</template>

<script>
import Header from './components/Header.vue'
import DiskList from './components/DiskList.vue'

export default {
  name: 'App',
  components: {
    Header,
    DiskList
  }
}
</script>

<style lang="scss">
@import '@/style/general.scss';
main {
  background-color: #1e2d3b;
  
}
</style>
