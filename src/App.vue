<template>
  <div id="app">
    <Header @search="getMoviesAndShows"/>
    <Main :searchedMovies="movies" :searchedTvShows="tvShows"/>

  </div>
</template>

<script>
import Header from './components/Header.vue'



import axios from 'axios';
import Main from './components/Main.vue';


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
    }
  },

  methods : {

    getMoviesAndShows : function(query){
      // Movies
      axios.get(`https://api.themoviedb.org/3/search/movie?api_key=1f3169b87aab636f5fde0cfa52d8788d&query=${query}`)
      .then((result) => {
        this.movies = result.data.results;
      })
      // Shows
      axios.get(`https://api.themoviedb.org/3/search/tv?api_key=1f3169b87aab636f5fde0cfa52d8788d&query=${query}`)
      .then((result) => {
        this.tvShows = result.data.results;
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
