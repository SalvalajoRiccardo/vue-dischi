<template>
  <div id="app">
    <div class="container-fluid">
      <div class="row">
        <header class="col-12">
          <Header />
        </header>
        
        <main class="col-12">
          <DiskList />
        </main>
      </div>
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
header {
  background: #2e3a46;
}
</style>
