<template>
    <div>
        <img :src="'https://image.tmdb.org/t/p/w154'+ posterSource" :alt="title">
        <h4>{{title}}</h4>
        <h5>{{originalTitle}}</h5>
        <p>{{refactorVote(averageVote)}}</p>
        <img class="language-flag" :src="getLanguageFlag(originalLanguage)" :alt="originalLanguage">
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

<style>

</style>