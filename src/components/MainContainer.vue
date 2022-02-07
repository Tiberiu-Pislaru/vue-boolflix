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
    overflow-x: auto;

    &::-webkit-scrollbar{
        display: none;
    }

    .card{
        margin-right: 15px;
        background: #000;
    }
}
</style>