<template>
    <div class='container' >
        <div class="card" v-for="movie in movies" :key="movie.id">
            <movie-card :card='movie' :flags="flagsArray"/>
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
        movies:Array,
        flagsArray:Array
    }
}
</script>

<style lang="scss" scoped>
.container{
    margin-top:30px;
    display: flex;
    flex-wrap: wrap;
    justify-content: space-around;
    background-color: #adadad;
    .card{
        width:calc(100% / 5 - 30px);
        margin-bottom: 15px;
        text-align: center;
        background: #333;
        padding-bottom:15px;
        // display: flex;
        // flex-direction: column;
        // justify-content: center;
       
    }
}
</style>