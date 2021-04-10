<template>
  <li @click="shortenDescription(film); displayInfo()">
    <p>{{film.title}}</p>
  </li>
</template>

<script>
import {eventBus} from '../main.js'

export default {
name:'film-item',
data() {
    return {
        shortDescription: ''
    }
},
props: [
  'film'
],
methods: {

    displayInfo: function() {
      eventBus.$emit("selected-film", this.film, this.shortDescription);
    },
    shortenDescription: function (film) {
        if (film.description.length > 350) {
            this.shortDescription = `${film.description.slice(0, 350)}...`
        } else {
            this.shortDescription = film.description
        }
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