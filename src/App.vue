<template>
  <div id="app">
    <KeywordShow />
  </div>
</template>

<script>
import KeywordShow from './components/keyword-show';
export default {
  name: 'App',
  components: {KeywordShow}
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  /* text-align: center; */
  color: #2c3e50;
  margin-top: 60px;
}
</style>
