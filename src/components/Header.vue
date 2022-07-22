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

    header {
        display: flex;
        justify-content: space-between;
        align-items: center;
        padding: 1rem;

        h1 {
            color: red;
        }

    }

</style>