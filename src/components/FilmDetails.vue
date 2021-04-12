<template>
  <section @click="filterCharacters(); changeFullDetails()">
      <h2>
        {{film.title}} - {{film.original_title}} ({{film.release_date}})
      </h2>
      <p>{{film.running_time}} mins</p>
      <p>{{description}}</p>
      <div>Click for more</div>
  </section>
</template>

<script>
import {eventBus} from '../main.js'

export default {
name: 'film-details',
data() {
    return {
        showFilmFull: false
    }
},
props: [
    "film",
    "description",
    "viewFilmFull",
    "characters"
],

methods: {
    filterCharacters: function() {

    },

    changeFullDetails: function() {
        this.showFilmFull = true;
        eventBus.$emit("change-show-full-details", this.showFilmFull)
    }
},
mounted() {

}
}
</script>

<style scoped>
    section{
        margin-top: 15px;
        width: 55%;
        position: fixed;
        right: 50px;
        height: fit-content;
        padding: 3px;
        cursor: pointer;
    }

    div {
        display: none;
        background: transparent;
        border: none;
        font-weight: bolder;
    }

    section:hover {
        background-color: rgb(162, 227, 227);
    }

    section:hover div {
        display: block;
    }
</style>