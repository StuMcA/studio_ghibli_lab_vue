<template>
  <div id="app">
    <header>
      <img src="./assets/studio-ghibli-logo.svg" alt="" id="logo">
    </header>
    <main>
      <film-list :films="films"/>
      <film-details v-if="selectedFilm" :film="selectedFilm" />
    </main>
  </div>
</template>

<script>
import {eventBus} from './main.js'
import FilmList from './components/FilmList.vue'
import FilmDetails from './components/FilmDetails.vue'

export default {
  name: 'App',
  data() {
    return {
      films: [],
      selectedFilm: null
    }
  },
  components: {
    "film-list": FilmList,
    "film-details": FilmDetails
  },
  methods: {
    getFilms: async function() {
      const results = await fetch('https://ghibliapi.herokuapp.com/films');
      const data = await results.json();
      this.films = data;
    }
  },
  mounted() {
    this.getFilms();

    eventBus.$on('selected-film', film => this.selectedFilm = film)
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
main {
  display: flex;
  flex-direction: row;
  justify-content: space-around;
}
</style>
