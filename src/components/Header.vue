<template>
    <header>
        <h1>BOOLFLIX</h1>
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
        }
    }

}
</script>

<style lang="scss" scoped>

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