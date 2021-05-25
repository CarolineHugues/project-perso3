<template>
  <div id="app">
    <Header />
    <HikingsInfos />
  </div>
</template>

<script>
import Header from './components/Header.vue';
import HikingsInfos from './components/HikingsInfos.vue';

export default {
  name: 'App',
  components: {
    Header,
    HikingsInfos
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
