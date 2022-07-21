<template>
  <div id="app">
    <SearchBar class="w-50" @search="log"/>
    <div>{{moviesTitle[1].title}}</div>
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

  data : function(){
    return {
      moviesTitle : [],
    }
  },

  methods : {
    log : function(string){
      console.log(string);
    },

    getMovies : function(query){
      axios.get(`https://api.themoviedb.org/3/search/movie?api_key=1f3169b87aab636f5fde0cfa52d8788d&query=${query}`)
      .then((result) => {
        this.moviesTitle = result.data.results;
        console.log(result.data.results[1].title);
      })
    }
  },

  created(){
    this.getMovies('back');
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
