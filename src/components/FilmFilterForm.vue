<template>
  <form @submit.prevent>
      <input type="text" placeholder="Start typing here to search..." @keyup="filterFilm" v-model="search">
  </form>
</template>

<script>
import {eventBus} from '../main.js'

export default {
name: "film-filter-form",
data() {
    return {
        "search": "",
        "filteredFilms": []
    }
},
props: [
    "films"
],

methods: {
    filterFilm: function () {
        let foundFilms = this.films.filter((film) => {
            return film.title.toLowerCase().indexOf(this.search.toLowerCase()) > -1
        })
        this.filteredFilms = foundFilms
        eventBus.$emit("filtered-films", this.filteredFilms)
    }
}

}
</script>

<style scoped>

input {
    padding-left: 30px;
    width: 100%;
    height: 40px;
    border: none;
    background: rgb(72, 107, 107);
    color: rgb(193, 248, 248);
    font-weight: bolder;
}

::placeholder {
    color: rgb(193, 248, 248);
    font-weight: bolder;
}

</style>