<template>
  <div id="app">
    <Header @search="findedResults"/>
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
    this.getHomeMovies();
    // this.getHomepage();
  },
  methods: {
    // getHomepage(getHomeMovies, getHomeSeries) {
    //   return getHomeMovies.concat(getHomeSeries);
    // },
    getHomeMovies() { //chiamata API delle cards a display nella 'home'
      axios.get(`https://api.themoviedb.org/3/discover/movie?sort_by=popularity.desc&api_key=f2ee1ac2d6b554f6a4a7b4304de1e553`).then((response) => { //chiamata API dei film più popolari
        this.movies = response.data.results; 
      })
    },
    // getHomeSeries() { -------CERCARE CODICE API
    //   axios.get(`https://api.themoviedb.org/3/discover/serie?sort_by=popularity.desc&api_key=f2ee1ac2d6b554f6a4a7b4304de1e553`).then((response) => { //chiamata API dei film più popolari
    //     this.series = response.data.results; 
    //   })
    // },
    findedResults(inputUser) {
      this.searchMovies(inputUser);
      this.searchTvSeries(inputUser);
    },
    searchMovies(inputUser) {
      // AXIOS - BEST PRACTICE:
      const params = {
        query: inputUser,
        api_key: 'f2ee1ac2d6b554f6a4a7b4304de1e553'
      }
        //axios.get(`https://api.themoviedb.org/3/search/movie?api_key=f2ee1ac2d6b554f6a4a7b4304de1e553&language=it_IT&query=${inputUser}`)
      axios.get(`https://api.themoviedb.org/3/search/movie?language=it_IT`, {params}).then((response) => {
        this.movies = response.data.results;
        // console.log(response)
      });
      return this.movies
    },
    searchTvSeries(inputUser) {
      const params = {
        query: inputUser,
        api_key: 'f2ee1ac2d6b554f6a4a7b4304de1e553',
      }
      axios.get(`https://api.themoviedb.org/3/search/tv?language=it_IT`, {params}).then((response) => {
        this.series = response.data.results;
      });
      return this.series;
    },
  }
}
</script>


<style lang="scss">
@import './style/main.scss';
@import url('https://fonts.googleapis.com/css2?family=Roboto:wght@100;300;400;500;700&display=swap');

</style>
