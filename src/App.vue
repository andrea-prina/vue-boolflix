<template>
  <div id="app">
    <SearchBar class="w-50" @search="getMoviesAndShows"/>
    <ul class="list-unstyled" id="movies">
      <li v-for="movie in movies" :key="movie.id">
        <DisplayCard
        :posterSource="movie.poster_path"
        :title="movie.title"
        :originalTitle="movie.original_title"
        :originalLanguage="movie.original_language"
        :averageVote="movie.vote_average"/>
      </li>
    </ul>
    <ul class="list-unstyled" id="tv-shows">
      <li v-for="show in tvShows" :key="show.id">
        <DisplayCard
        :posterSource="show.poster_path"
        :title="show.name"
        :originalTitle="show.original_name"
        :originalLanguage="show.original_language"
        :averageVote="show.vote_average"/>
      </li>
    </ul>
  </div>
</template>

<script>
import SearchBar from './components/SearchBar.vue'
import DisplayCard from './components/DisplayCard.vue'

import axios from 'axios';


export default {
  name: 'App',
  components: {
    SearchBar,
    DisplayCard,
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
