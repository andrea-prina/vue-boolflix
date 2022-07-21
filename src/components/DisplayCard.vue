<template>
    <div>
        <img :src="posterSource" :alt="title">
        <h4>{{title}}</h4>
        <h5>{{originalTitle}}</h5>
        <img class="language-flag" :src="flagSource" :alt="originalLanguage">
        <p>{{averageVote}}</p>
    </div>
</template>

<script>
export default {

    props : {
        
        posterSource : String,
        title : String,
        originalTitle : String,
        originalLangue : String,
        flagSource : String,
        averageVote : Number,

    }

}
</script>

<style>

</style>