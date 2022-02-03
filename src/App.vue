<template>
  <div id="app">
    <search-box @search='getMovies'/>
    <main-container :movies='moviesList' :flagsArray='listFlags'/>
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
    getMovies(string){
      
      if (!string==''){

        axios.get("https://api.themoviedb.org/3/search/movie?query="+string+"&api_key=f760cceed080dd564aa1a8619b8ac208").then((result)=>{
          this.moviesList=result.data.results;
        })
      }
     
    }
  },
  data(){
    return {
      moviesList:[],
      listFlags:['de','en','es','fr','hi','id','ja','pt','ro','ru','zh']
    }
  }
}
</script>

<style lang="scss">
*{
  padding: 0;
  margin: 0;
  box-sizing: border-box;
}
body{
  background-color: #adadad;
}
</style>
