<template>
  <section>
      <ul>
          <film-item v-for="(film) in films" :key="film.id" :film="film" />
      </ul>
  </section>
</template>

<script>
import FilmItem from './FilmItem.vue'

export default {
name: 'film-list',
components: {
    'film-item': FilmItem
},
props: ['films']
}
</script>

<style>

</style>