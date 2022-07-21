<template>
  <div id="app">
    <SearchBar class="w-50" @search="getMoviesAndShows"/>
    <ul id="movies">
      <li v-for="(movie, index) in movies" :key="index">
        <h4>{{movie.title}}</h4>
        <h5>{{movie.original_title}}</h5>
        <img class="language-flag" :src="getLanguageFlag(movie.original_language)" :alt="movie.original_language">
        <p>{{movie.vote_average}}</p>
      </li>
    </ul>
    <ul id="tv-shows">
      <li v-for="(show, index) in tvShows" :key="index">
        <h4>{{show.name}}</h4>
        <h5>{{show.original_name}}</h5>
        <img class="language-flag" :src="getLanguageFlag(show.original_language)" :alt="show.original_language">
        <p>{{show.vote_average}}</p>
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


    getLanguageFlag : function(langCode){

      let flagIcon = "";

      switch (langCode){
        // TODO: Map more languages
        case 'en' :
          flagIcon = "gb";
          break;

        case 'it' :
          flagIcon = "it";
          break;

        case 'ja' :
          flagIcon = "jp";
          break
        
        }
      
      return (`https://countryflagsapi.com/png/${flagIcon}`)
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

  #movies {
    color: yellow;
  }

  #tv-shows{
    color: cyan;
  }

  .language-flag {
    width: 20px;
  }




</style>
