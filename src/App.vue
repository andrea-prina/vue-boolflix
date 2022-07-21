<template>
  <div id="app">
    <SearchBar class="w-50"/>
  </div>
</template>

<script>
import SearchBar from './components/SearchBar.vue'

import axios from 'axios';


export default {
  name: 'App',
  components: {
    SearchBar,
  }
}
</script>

<style lang="scss">

  @import '~bootstrap/scss/bootstrap';

  #app{
    background-color: black;
    color: white;
    height: 100vh;
  }

</style>
