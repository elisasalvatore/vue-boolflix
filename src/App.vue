<template>
  <div id="app">
    <Header @filter="filterTitles"/>
    <MainContainer :movies="movies"/>
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
    }
  },
  methods: {
    filterTitles(inputUser) {
      axios.get(`https://api.themoviedb.org/3/search/movie?api_key=f2ee1ac2d6b554f6a4a7b4304de1e553&query=${inputUser}`).then((response) => {
        this.movies = response.data.results;
      });
      // console.log(this.movies)
      return this.movies
    },
  }
}
</script>


<style lang="scss">
@import './style/main.scss';
@import url('https://fonts.googleapis.com/css2?family=Roboto:wght@100;300;400;500;700&display=swap');

</style>
