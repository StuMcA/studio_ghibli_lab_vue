<template>
  <div id="app">
    <header>
      <img src="./assets/studio-ghibli-logo.svg" alt="" id="logo">
    </header>
    <main>
      <film-list :films="films"/>
      <film-details 
        v-if="selectedFilm" 
        :film="selectedFilm" 
        :description="shortDescription"
        :viewFilmFull="viewFilmFull"
        :characters="characters"
        />
      <film-full-details v-if="viewFilmFull" :film="selectedFilm" :characters="characters"/>
    </main>
  </div>
</template>

<script>
import {eventBus} from './main.js'
import FilmList from './components/FilmList.vue'
import FilmDetails from './components/FilmDetails.vue'
import FilmFullDetails from './components/FilmFullDetails.vue'

export default {
  name: 'App',
  data() {
    return {
      films: [],
      selectedFilm: null,
      shortDescription: "",
      viewFilmFull: false,
      characters: [],
      filteredCharacters: []
    }
  },
  components: {
    "film-list": FilmList,
    "film-details": FilmDetails,
    "film-full-details": FilmFullDetails
  },
  methods: {
    getFilms: async function() {
      const results = await fetch('https://ghibliapi.herokuapp.com/films');
      const data = await results.json();
      this.films = data;
    },
    getCharacters: async function() {
      const results = await fetch('https://ghibliapi.herokuapp.com/people');
      const data = await results.json();
      this.characters = data;
    }
  },
  mounted() {
    this.getFilms();
    this.getCharacters();

    eventBus.$on("selected-film", (film, description) => {
      this.selectedFilm = film
      this.shortDescription = description
      });

    eventBus.$on("change-show-full-details", (boolean) => this.viewFilmFull = boolean)
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  
}

#logo {
  display: block;
  width: 300px;
  margin: 5px auto 20px auto;
}
body {
  background-color: rgb(193, 248, 248);
  margin: 0;
}
main {
  display: flex;
  flex-direction: row;
  justify-content: space-between;
}
</style>
