<template>
  <section>
      <ul>
          <li v-for="(film, id) in films" :key="id" :film="film">
              <film-item />
          </li>
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