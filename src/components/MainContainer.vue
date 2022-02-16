<template>
    <div class="container">
        <div class="card" v-for="video in videos" :key="video.id">
            <movie-card :card='video' :flags="flagsArray"/>
        </div>
    </div>
</template>

<script> 
import MovieCard from './MovieCard.vue'
export default {
    components: {
        MovieCard,
    },
    props: {
        videos:Array,
        flagsArray:Array
    }
}
</script>

<style lang="scss" scoped>


.container{
    display: flex;
    overflow-x: scroll;
    padding: 80px 40px;

    &::-webkit-scrollbar{
        display: none;
    }

    .card{
        display: grid;
        &:hover{
            transform: scale(1.3);
            z-index: 999;
            transition: all .5s;
        }
    }
}
</style>