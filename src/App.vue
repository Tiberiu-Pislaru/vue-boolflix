<template>
  <div id="app">
    <search-box @search='getMovies'/>
    <main-container :movies='moviesList'/>
  </div>
</template>

<script>
import axios from 'axios'
import SearchBox from './components/SearcheBox.vue'
import MainContainer from './components/MainContainer.vue'

export default {
  name: 'App',
  components: {
    SearchBox,
    MainContainer,
  },
  methods: {
    getMovies(){
      axios.get('https://api.themoviedb.org/3/search/movie?query=ritorno&api_key=f760cceed080dd564aa1a8619b8ac208').then((result)=>{
        this.moviesList=result.data.results;
        console.log(this.moviesList)
      })
    }
  },
  data(){
    return {
      moviesList:[]
    }
  }
}
</script>

<style lang="scss">

</style>
