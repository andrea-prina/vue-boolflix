<template>
  <div id="app">
    <Header @search="getMoviesAndShows"/>
    <Main
    :searchedMovies="movies"
    :searchedTvShows="tvShows"
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
      movies : {
        list : [],
        genres : [],
      },

      tvShows : {
        list : [],
        genres : [],
      },

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
          this.movies.list = result.data.results;
          this.newPage = false;
        })
        .catch((err) => {
          console.warn(err);
        })
        // Shows
        axios.get(`https://api.themoviedb.org/3/search/tv?api_key=${this.apiKey}&query=${query}`)
        .then((result) => {
          this.tvShows.list = result.data.results;
        })
        .catch((err) => {
          console.warn(err);
        })
    
      }

    },

  },

  created(){
      axios.get(`https://api.themoviedb.org/3/genre/movie/list?api_key=${this.apiKey}`)
      .then((result) => {
        this.movies.genres = result.data.genres;
      })

      axios.get(`https://api.themoviedb.org/3/genre/tv/list?api_key=${this.apiKey}`)
      .then((result) => {
        this.tvShows.genres = result.data.genres;
      })
  }
}

</script>

<style lang="scss">

  @import '~bootstrap/scss/bootstrap';
  @import url('https://fonts.googleapis.com/css2?family=Bebas+Neue&display=swap');
  @import './assets/styles/variables.scss';

  body {
    background-color: $backgroundColor;
    color: $mainTextColor;
  }

</style>
