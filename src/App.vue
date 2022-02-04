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

    async getMovies(query){
      this.moviesList= await this.getAPI('movie',query);
    },
    async getSeries(query){
      this.seriesList= await this.getAPI('movie',query);
    },
    async getAPI(type, query){
      
      const params = {
        query:query,
        api_key:'f760cceed080dd564aa1a8619b8ac208'
      }

      if (!query==''){

        const result = await axios.get(`https://api.themoviedb.org/3/search/${type}`,{params}).then((result)=>{
          return result.data.results;
        })
        return result
      }
     
    }
  },
  data(){
    return {
      moviesList:[],
      seriesList:[],
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
