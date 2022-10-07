<template>
    <header>
        <h1><a href="" @search="resetQuery">BOOLFLIX</a></h1>
        <SearchBar class="w-25" @search="passQueryToParent"/>
    </header>
</template>

<script>
import SearchBar from './SearchBar.vue'

export default {

    components : {
        SearchBar,
    },

    methods : {
        passQueryToParent : function(query){
            this.$emit('search', query);
        },

        resetQuery : function(){
            this.$emit('search', '');
        }
    }

}
</script>

<style lang="scss" scoped>

    @import '../assets/styles/variables.scss';

    header {
        display: flex;
        justify-content: space-between;
        align-items: center;
        padding: 0 1rem;

        h1 > a {
            margin: 0;
            color: $brandColor;
            font-family: 'Bebas Neue', cursive;
            font-size: 4.5rem;
            text-decoration: none;
        }

    }

</style>