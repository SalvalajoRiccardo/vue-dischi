<template>
  <div id="app">
      
  <Header />

  <main>
    <DiskList />
  </main>
    
    
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
  padding: 50px;
  
}

</style>
