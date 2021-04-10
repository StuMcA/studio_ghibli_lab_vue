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
  console.log(this.film);
  eventBus.$emit("selected-film", this.film);
}
}
}
</script>

<style scoped>

li {
  list-style: none;
  cursor: pointer;
}

li:hover {
  background-color: rgb(162, 227, 227);
}
</style>>

</style>