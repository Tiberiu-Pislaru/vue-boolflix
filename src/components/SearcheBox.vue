<template>
    <header>
        <input type="text" v-model="inputSearch">
        <button @click="$emit('search', inputSearch)">&#128270;</button>
    </header>
</template>

<script>
export default {
    data(){
        return{
            inputSearch: '',
        }
    }
}
</script>

<style lang="scss" scoped>
header{
    position: sticky;
    display: flex;
    align-items: center;
    top: 0;
    left: 15px;
    button{
        all:unset;
        cursor: pointer;
        font-size: 30px;
    }
}
</style>