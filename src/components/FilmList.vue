<template>
      <ul>
          <film-item v-for="(film) in filteredFilms" :key="film.id" :film="film" />
          <!-- <film-item v-if="filteredFilms" v-for="(film) in films" :key="film.id" :film="film" /> -->
      </ul>
</template>

<script>
import FilmItem from './FilmItem.vue'

export default {
name: 'film-list',
components: {
    'film-item': FilmItem
},
props: [
    'films',
    'filteredFilms'
]
}
</script>

<style scoped>
ul {
    width: fit-content;
}
</style>