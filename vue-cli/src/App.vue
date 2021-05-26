<template>
  <div id="app">
    <Header />
    <Hikings />
  </div>
</template>

<script>
import Header from './components/Header.vue';
import Hikings from './components/Hikings.vue';


export default {
  name: 'App',
  components: {
    Header,
    Hikings
  },
}
</script>

<style>
html, body, #app {
  margin: 0;
  padding: 0;
}
</style>
