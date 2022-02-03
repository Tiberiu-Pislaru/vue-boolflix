<template>
    <div class='container' >
        <div class="card" v-for="movie in movies" :key="movie.id">
            <movie-card :card='movie'/>
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
        movies:Array
    }
}
</script>

<style lang="scss" scoped>
.container{
    display: flex;
    flex-wrap: wrap;
    justify-content: space-around;
    .card{
        width:calc(100% / 5 - 30px);
        margin-bottom: 15px;
        text-align: center;
        background: #333;
       
    }
}
</style>