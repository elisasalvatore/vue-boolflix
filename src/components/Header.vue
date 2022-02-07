<template>
  <header>
    <div class="title">Boolflix</div>

    <div class="hd-right">
      <div class="homepage-buttons">
        <button class="bt-movies">FILM</button> 
        <button class="bt-series">SERIE TV</button> 
      </div> 

      <div class="search-bar">
        <input v-model="inputUser" type="text" placeholder="Cerca"> 
        <button @click="$emit('search', inputUser)">Cerca</button>
      </div>
    </div>
  </header>
</template>

<script>
export default {
  data() {
    return {
      inputUser:'',
    }
  },
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

  .title {
    color: red;
    text-transform: uppercase;
    font-size: 40px;
    font-weight: bold;
    cursor: pointer;
  }

  .hd-right {
    display: flex;
    align-items: center;

    .homepage-buttons { 
      margin: 0 20px;

      button {
        margin-left: 10px;
        padding: 5px 10px;
        border: none;
        border-radius: 20px;
        background-color: #333;
        color: red;
        font-size: 15px;
        font-weight: 600;
        cursor: pointer;

        &:hover {
          background-color: #fff;
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
}
</style>
