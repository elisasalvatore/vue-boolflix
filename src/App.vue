<template>
  <div id="app">
    <Header @search="inputResults" />
    <MainContainer :movies="movies" :series="series"/>
  </div>
</template>

<script>
import axios from 'axios'
import Header from '@/components/Header.vue'
import MainContainer from '@/components/MainContainer.vue'

export default {
  name: 'App',
  components: {
    Header,
    MainContainer,
  },
  data() {
    return {
      movies: [],
      series: [],
    }
  },
  mounted() { 
    this.getHomepage();
  },
  methods: {
    getHomepage() {
      this.getPopularMovies();
      this.getPopularSeries();
    },
    getPopularMovies() { //chiamata API dei film più popolari
      axios.get(`https://api.themoviedb.org/3/movie/popular?api_key=f2ee1ac2d6b554f6a4a7b4304de1e553&language=it-IT&page=1`).then((response) => {
        this.movies = response.data.results; 
      })
    },
    getPopularSeries() { //chiamata API delle serie televisive più popolari
      axios.get(`https://api.themoviedb.org/3/tv/popular?api_key=f2ee1ac2d6b554f6a4a7b4304de1e553&language=it-IT&page=1`).then((response) => {
        this.series = response.data.results; 
      })
    },
    inputResults(inputUser) {
      // AXIOS -- BEST PRACTICE
      const params = {
        query: inputUser,
        api_key: 'f2ee1ac2d6b554f6a4a7b4304de1e553',
      }
      // SEARCHING FILM
      axios.get(`https://api.themoviedb.org/3/search/movie?language=it_IT`, {params}).then((response) => {
        //axios.get(`https://api.themoviedb.org/3/search/movie?api_key=f2ee1ac2d6b554f6a4a7b4304de1e553&language=it_IT&query=${inputUser}`)
        this.movies = response.data.results;
      })
      // SEARCHING TV SERIES
      axios.get(`https://api.themoviedb.org/3/search/tv?language=it_IT`, {params}).then((response) => {
        this.series = response.data.results;
      })
    },
  },
}
</script>

<style lang="scss">
@import './style/main.scss';
@import url('https://fonts.googleapis.com/css2?family=Roboto:wght@100;300;400;500;700&display=swap');

</style>
