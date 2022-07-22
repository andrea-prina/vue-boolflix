<template>
  <div id="app">
    <Header @search="getMoviesAndShows"/>
    <Main
    :searchedMovies="movies"
    :checkMovies="foundMovies"
    :searchedTvShows="tvShows"
    :checkShows="foundTvShows"
    :newPage="newPage"/>

  </div>
</template>

<script>
import Header from './components/Header.vue'
import Main from './components/Main.vue';

import axios from 'axios';


export default {
  name: 'App',
  components: {
    Header,
    Main,
  },

  data : function(){
    return {
      movies : [],
      tvShows : [],
      foundMovies : false,
      foundTvShows : false,
      newPage : true,
      apiKey : "1f3169b87aab636f5fde0cfa52d8788d",
    }
  },

  methods : {

    getMoviesAndShows : function(query){

      if (query != "" || query === null){

        // Movies
        axios.get(`https://api.themoviedb.org/3/search/movie?api_key=${this.apiKey}&query=${query}`)
        .then((result) => {
          this.movies = result.data.results;
          if (this.movies.length > 0){
            this.foundMovies = true;
          } else {
            this.foundMovies = false;
          }
          this.newPage = false;
        })
        .catch((err) => {
          console.warn(err);
        })
        // Shows
        axios.get(`https://api.themoviedb.org/3/search/tv?api_key=${this.apiKey}&query=${query}`)
        .then((result) => {
          this.tvShows = result.data.results;
          if (this.tvShows.length > 0){
            this.foundTvShows = true;
          } else {
            this.foundTvShows = false;
          }
        })
        .catch((err) => {
          console.warn(err);
        })
    
      }

    },

  },

}
</script>

<style lang="scss">

  @import '~bootstrap/scss/bootstrap';
  @import url('https://fonts.googleapis.com/css2?family=Bebas+Neue&display=swap');

  body {
    background-color: black;
    color: white;
  }

</style>
