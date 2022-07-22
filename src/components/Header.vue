<template>
    <div>
        <h1>BOOLFLIX</h1>
        <SearchBar class="w-50" @search="passQueryToParent"/>
    </div>
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

<style>


</style>