<template>
  <li @click="displayInfo">
    <p>{{film.title}}</p>
  </li>
</template>

<script>
import {eventBus} from '../main.js'

export default {
name:'film-item',
props: [
  'film'
],
methods: {

displayInfo: function() {
  eventBus.$emit('film-selected', this.film)
}
}
}
</script>

<style scoped>

li {
  list-style: none;
}
</style>>

</style>