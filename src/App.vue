<template>
  <div id="app">
    <header>
      <img src="./assets/studio-ghibli-logo.svg" alt="" id="logo">
    </header>
    <main>
      <film-list />
    </main>
  </div>
</template>

<script>
import FilmList from './components/FilmList.vue'

export default {
  name: 'App',
  components: {
    "film-list": FilmList
  },
  methods: {

  },
  mounted() {

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

#logo {
  width: 300px;
}
body {
  background-color: rgb(193, 248, 248);
}
</style>
