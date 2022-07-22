<template>
    <div>
        <input v-model="searchQuery" type="text" placeholder="Search movie or TV series">
        <button @click="$emit('search', searchQuery)"><i class="fa-solid fa-magnifying-glass"></i></button>
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
        border: 0;
        border-bottom: 0.25px solid rgb(40, 40, 40);
        color: white;
        background-color: black;
    }

    button {
        width: 15%;
        color: white;
        border: 0;
        background-color: black;
    }

</style>