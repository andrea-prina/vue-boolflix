<template>
  <div id="app">
    <SearchBar class="w-50" @search="log"/>
  </div>
</template>

<script>
import SearchBar from './components/SearchBar.vue'

import axios from 'axios';


export default {
  name: 'App',
  components: {
    SearchBar,
  },

  methods : {
    log : function(string){
      console.log(string);
    }
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
