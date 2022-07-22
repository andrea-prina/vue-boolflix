<template>
    <div>
        <input class="main-colors" v-model.trim="searchQuery" type="text" placeholder="Search movie or TV series">
        <button class="main-colors" @click="$emit('search', searchQuery)"><i class="fa-solid fa-magnifying-glass"></i></button>
    </div>
</template>

<script>
export default {

    data : function(){

        return {
            searchQuery : "",
        }
    }

}
</script>

<style lang="scss" scoped>

    @import '../assets/styles/variables.scss';

    input[type='text']{
        width: 85%;
        border: 0;
        border-bottom: 0.25px solid $accentColor;
    }

    button {
        width: 15%;
        border: 0;
    }

    .main-colors {
        background-color: $backgroundColor;
        color: $mainTextColor;
    }

</style>