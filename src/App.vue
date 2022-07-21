<template>
  <div id="app">
    <SearchBar class="w-50" @search="getMovies"/>
    <ul>
      <li v-for="(element, index) in movies" :key="index">
        <h4>TITLE</h4>
        <h5>Original title</h5>
        <p>Language</p>
        <p>Rating</p>
      </li>
    </ul>
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
      movies : [],
    }
  },

  methods : {
    log : function(string){
      console.log(string);
    },

    getMovies : function(query){
      axios.get(`https://api.themoviedb.org/3/search/movie?api_key=1f3169b87aab636f5fde0cfa52d8788d&query=${query}`)
      .then((result) => {
        this.movies = result.data.results;
      })
    },
  },

}
</script>

<style lang="scss">

  @import '~bootstrap/scss/bootstrap';

  body {
    background-color: black;
    color: white;
  }


</style>
