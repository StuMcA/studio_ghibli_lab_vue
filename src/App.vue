<template>
  <div id="app">
    <header>
      <img src="./assets/studio-ghibli-logo.svg" alt="" id="logo">
    </header>
    <main>
      <film-list :films="films"/>
    </main>
  </div>
</template>

<script>
import FilmList from './components/FilmList.vue'

export default {
  name: 'App',
  data() {
    return {
      films: []
    }
  },
  components: {
    "film-list": FilmList
  },
  methods: {
  
  },
  async mounted() {
    const results = await fetch('https://ghibliapi.herokuapp.com/films');
    const data = await results.json();
    this.films = data;
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
