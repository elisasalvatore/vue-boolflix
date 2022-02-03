<template>
  <header>
    <div class=title>Boolflix</div> 

    <div>
      <input v-model="inputUser" type="text" placeholder="Search"> 
      <button @click="$emit('filter', inputUser)">Cerca</button>
    </div>
  </header>
</template>

<script>
export default {
  data() {
    return{
      inputUser:''
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
  }

  button {
    margin-left: 10px;
  }
}
</style>
