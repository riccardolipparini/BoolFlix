<template>
  <div id="app">
    <Search @ricercaMoviesSeries="searchingMoviesSeries"
     />
    <Cards :detailsMovies="movies"
    :detailsSeries="series"
    />
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
      apiUrlFilms: `https://api.themoviedb.org/3/search/movie?api_key=e99307154c6dfb0b4750f6603256716d&query=`,
      apiUrlSeries: `https://api.themoviedb.org/3/search/tv?api_key=e99307154c6dfb0b4750f6603256716d&language=it_IT&query=`,
      movies: [],
      series: [],
      searchText: "",
    }
  },
  methods:{
    getMovies(){
      axios
      .get(this.apiUrlFilms + this.searchText)
      .then((result) => {
        this.movies = result.data.results
      })
    },
    getSeries(){
      axios
      .get(this.apiUrlSeries + this.searchText)
      .then((result) => {
        this.series = result.data.results
      })
    },
    
    searchingMoviesSeries(titoloFilm){
      this.searchText = titoloFilm;
      this.getMovies();
      this.getSeries();
    },
    
  }
 
}
</script>

<style lang="scss">

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  background-color: black;
}
body{
  background-color: black;
}
</style>
