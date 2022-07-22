<template>
    <header>
        <h1>BOOLFLIX</h1>
        <SearchBar class="w-50" @search="passQueryToParent"/>
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
        }
    }

}
</script>

<style lang="scss">

    @import url('https://fonts.googleapis.com/css2?family=Bebas+Neue&display=swap');

    header {
        display: flex;
        justify-content: space-between;
        align-items: center;
        padding: 0 1rem;

        h1 {
            margin: 0;
            color: red;
            font-family: 'Bebas Neue', cursive;
            font-size: 4.5rem;
        }

    }

</style>