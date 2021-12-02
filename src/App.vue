<template>
  <div id="app">
    <Search @ricerca="searching" />
    <Cards :details="movies"/>
  </div>
</template>

<script>
import Search from './components/Search.vue'
import Cards from './components/Cards.vue'
import axios from "axios"

export default {
  name: 'App',
  components: {
    Search,
    Cards,
  },
  data(){
    return {
      apiUrl: `https://api.themoviedb.org/3/search/movie?api_key=e99307154c6dfb0b4750f6603256716d&query=`,
      movies: [],
      searchText: "",
    }
  },
  methods:{
    getMovies(){
      axios
      .get(this.apiUrl + this.searchText)
      .then((result) => {
        this.movies = result.data.results
      })
    },
    searching(titoloFilm){
      this.searchText = titoloFilm;
      this.getMovies();
    }
  }
 
}
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
}
</style>
