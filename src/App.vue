<template>
  <div id="app">
    <Header />
    <MainContainer/>
  </div>
</template>

<script>
import Header from '@/components/Header.vue'
import MainContainer from '@/components/MainContainer.vue'

export default {
  name: 'App',
  components: {
    Header,
    MainContainer,
  }
}
</script>

<style lang="scss">
@import './style/main.scss';

</style>
