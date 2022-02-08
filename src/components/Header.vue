<template>
  <header>
    <div class="hd-left">
      <div class="title">Boolflix</div>

      <ul>
        <li>Home</li>
        <li>Serie TV</li>
        <li>Film</li>
        <li>Aggiunti di recente</li>
      </ul>
    </div>

    <div class="search-bar">
      <input v-model="inputUser" @keyup.enter="$emit('search', inputUser)" type="text" placeholder="Cerca"> 
      <button @click="$emit('search', inputUser)">Cerca</button>
    </div>
  </header>
</template>

<script>
import axios from 'axios'

export default {
  data() {
    return {
      inputUser:'',
    }
  },
  methods: {
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
  }
}
</script>

<style scoped lang="scss">
header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  height: 80px;
  padding: 0 20px;
  background-color: rgb(19, 18, 18);


  .hd-left {
    display: flex;
    align-items: center;

    .title {
      color: red;
      text-transform: uppercase;
      font-size: 40px;
      font-weight: bold;
    }

    ul {
      display: flex;
      padding: 0 20px;

      li {
        list-style: none;
        color: #ccc;
        padding: 0 5px;
        cursor: pointer;

        &:hover {
          color: #fff;
        }
      }
    }
  }  

  .search-bar {
    input {
      padding: 3px;
    }

    button {
      padding: 3px 5px;
      margin-left: 10px;
    }
  }
}
</style>
