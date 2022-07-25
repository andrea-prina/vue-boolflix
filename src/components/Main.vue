<template>
    <main>

        <!-- Create movie cards -->
        <div v-if="searchedMovies.length > 0">
            <h4>Movies</h4>
            <ul class="list-unstyled d-flex">
                <li v-for="movie in searchedMovies" :key="movie.id">
                    <DisplayCard
                    :posterSource="movie.poster_path"
                    :title="movie.title"
                    :originalTitle="movie.original_title"
                    :originalLanguage="movie.original_language"
                    :averageVote="movie.vote_average"
                    :overview="movie.overview"/>
                </li>
            </ul>
        </div>

        <!-- Create tv shows cards -->
        <div v-if="searchedTvShows.length > 0">
            <h4>TV Shows</h4>
            <ul class="list-unstyled d-flex">
                <li v-for="show in searchedTvShows" :key="show.id">
                    <DisplayCard
                    :posterSource="show.poster_path"
                    :title="show.name"
                    :originalTitle="show.original_name"
                    :originalLanguage="show.original_language"
                    :averageVote="show.vote_average"
                    :overview="show.overview"/>
                </li>
            </ul>
        </div>

        <h4 v-if="searchedMovies.length === 0 && searchedTvShows.length === 0 && !newPage">We couldn't find anything...</h4>

    </main>
</template>

<script>
import DisplayCard from './DisplayCard.vue'

export default {

    components : {
        DisplayCard,
    },

    props : {
        searchedMovies : Array,
        searchedTvShows : Array,
        newPage : Boolean,
    }

}
</script>

<style lang="scss">

    main {
        padding: 0 1rem;

        ul {
            padding-bottom: 3rem;
            overflow-x: auto;
    
            li {
                margin-right: 0.2rem;
            }
        }

        h4 {
            font-weight: bold;
        }
    }

    .language-flag {
        width: 20px;
    }

    
</style>