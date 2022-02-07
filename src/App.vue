<template>
  <div id="app">
    <header-box @search='getTVAndMovies'/>
    <main-container :videos='allVideos' :flagsArray='listFlags'/>
  </div>
</template>

<script>
import axios from 'axios'
import HeaderBox from './components/SearcheBox.vue'
import MainContainer from './components/MainContainer.vue'

export default {
  name: 'App',
  components: {
    HeaderBox,
    MainContainer,
  },
  methods: {

    async getTVAndMovies(query){
      await this.getMovies(query);
      await this.getSeries(query);
      this.allVideos=[...this.moviesList,...this.seriesList];
      console.log(this.allVideos)
    },

    async getMovies(query){
      this.moviesList= await this.getAPI('movie',query);
    },
    async getSeries(query){
      this.seriesList= await this.getAPI('tv',query);
    },
    async getAPI(type, query){
      
      const params = {
        query:query,
        api_key:'f760cceed080dd564aa1a8619b8ac208',
        include_adult:false
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
      listFlags:['de','en','es','fr','ja','pt','ro','ru','zh'],
      allVideos:[]
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
  background-color: #0f0f0f;
}
#app{
  margin: 15px;
}
</style>
