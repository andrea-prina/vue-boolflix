<template>
    <div class="display-card">

        <img class="poster-img" :src="'https://image.tmdb.org/t/p/w342'+ posterSource" :alt="title">

        <div class="card-info">
            <h4>{{title}}</h4>
            <p v-if="title != originalTitle"><strong>Original title</strong>: {{originalTitle}}</p>
            <p><strong>Rating</strong>: 
                <i v-for="(n, index) in refactorVote(averageVote)" class="fa-solid fa-star" :key="'A'+index"></i>
                <i v-for="(n, index) in (this.MAX_VOTE - refactorVote(averageVote))" class="fa-regular fa-star" :key="'B'+index"></i>
            </p>
            <p>
                <strong>Genres</strong>: 
                <span>{{genres[0]}}</span>
                <span v-for="(genre, index) in genres.slice(1)" :key="index">, {{genre}}</span>
            </p>
            <span><strong>Language </strong></span><img class="language-flag" :src="getLanguageFlag(originalLanguage)" :alt="originalLanguage">
            <p class="pt-2"><strong>Overview</strong>: {{overview}}</p>
        </div>
    
    </div>
</template>


<script>
export default {

    props : {
        
        posterSource : String,
        title : String,
        originalTitle : String,
        originalLanguage : String,
        flagSource : String,
        averageVote : Number,
        overview : String,
        genres : Array,

    },

    data : function(){
        return{
            MAX_VOTE : 5,
        }
    },

    methods : {

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
                break;
            }

            return (`https://countryflagsapi.com/png/${flagIcon}`)
        },

        refactorVote : function(vote){
            // Change the vote system from 1-10 to 1-5 (rounding up to integers) to display it as stars
            return Math.ceil(vote / 2);
        }
    }

}
</script>

<style lang="scss" scoped>

    @import '../assets/styles/variables.scss';

    .display-card {
        width: 342px;
        height: 514px;
        border: 0.25px solid $accentColor;
        overflow-y: auto;


        .poster-img {
            width: 100%;
            height: 100%;
            object-fit: cover;

            // Format for alt text and image when poster is missing
            display: inline-block;
            text-align: center;
            font-weight: bold;
            background-image: url('../assets/img/miss-image.png');
            background-position: center;
            background-repeat: no-repeat;
        }
    }

    .card-info {
        padding: 1rem;
        display: none;

        p {
            margin: 0;
        }
    }

    .language-flag {
        height: 1.2rem;
    
    }

    .display-card:hover {

        .card-info {
            display: inline-block;
        }

        .poster-img {
            display: none;
        }
    }

</style>