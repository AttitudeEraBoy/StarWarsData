<template>
  <div id="app">
    <headerz></headerz>
    <router-view></router-view>
  </div>
</template>

<script>
import Informations from './components/Informations.vue'
import Movies from './components/Movies.vue';
import Header from './components/header.vue';
export default {
  name: 'app',
  components: {
    'inform':Informations,
    'movies':Movies,
    'headerz':Header
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
