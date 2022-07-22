<template>
    <div>
        <ul class="list-unstyled d-flex">
            <li v-for="movie in searchedMovies" :key="movie.id">
                <DisplayCard
                :posterSource="movie.poster_path"
                :title="movie.title"
                :originalTitle="movie.original_title"
                :originalLanguage="movie.original_language"
                :averageVote="movie.vote_average"/>
            </li>
        </ul>
        <ul class="list-unstyled d-flex">
            <li v-for="show in searchedTvShows" :key="show.id">
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
import DisplayCard from './DisplayCard.vue'

export default {

    components : {
        DisplayCard,
    },

    props : {
        searchedMovies : Array,
        searchedTvShows : Array,
    }

}
</script>

<style lang="scss">

    .language-flag {
        width: 20px;
    }

    li {
        margin: 0.5rem;
    }

    ul {
        overflow-x: auto;
    }
</style>