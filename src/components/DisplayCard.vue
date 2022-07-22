<template>
    <div class="display-card">
        <img :src="'https://image.tmdb.org/t/p/w342'+ posterSource" :alt="title">
        <div class="card-info">
            <h4>{{title}}</h4>
            <h5>{{originalTitle}}</h5>
            <p>
                <i v-for="(n, index) in refactorVote(averageVote)" class="fa-solid fa-star" :key="'A'+index"></i>
                <i v-for="(n, index) in (this.MAX_VOTE - refactorVote(averageVote))" class="fa-regular fa-star" :key="'B'+index"></i>
            </p>
            <img class="language-flag" :src="getLanguageFlag(originalLanguage)" :alt="originalLanguage">
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

<style lang="scss">

    .display-card {
        width: 342px;
        height: 514px;

        img {
            width: 100%;
            height: 100%;
            object-fit: cover;
            display: inline-block;
        }
    }

    .card-info {
        display: none;
    }

    .display-card:hover {

        .card-info {
            display: inline-block;
        }

        img {
            display: none;
        }
    }



</style>