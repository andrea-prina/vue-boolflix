<template>
    <div>
        <input v-model="searchQuery" type="text" placeholder="Search movie or TV series">
        <button @click="$emit('search', searchQuery)">Search</button>
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

    input[type='text']{
        width: 85%;
    }

    button {
        width: 15%;
    }

</style>