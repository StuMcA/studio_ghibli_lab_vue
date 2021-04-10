<template>
    <div>
        <section>
            <button @click="changeFullDetails">Close</button>
            <header>
                <h1>{{film.title}} ({{film.release_date}})</h1>
                <h4>{{film.running_time}} mins</h4>
                <h3>{{film.original_title_romanised}} ({{film.original_title}})</h3>
            </header>
            <main>
                <p>Directed by: {{film.director}}</p>
                <p>Produced by: {{film.producer}}</p>
            </main>

            <p>{{film.description}}</p>
        </section>
    </div>

</template>

<script>
import {eventBus} from '../main.js'

export default {
name: "film-full-details",
props: [
    "film"
],
methods: {
    changeFullDetails: function() {
        this.showFilmFull = false;
        eventBus.$emit("change-show-full-details", this.showFilmFull)
    }
}
}
</script>

<style scoped>

div {
    position: fixed;
    top: 0;
    width: 100%;
    height: 100%;
    background-color: rgba(0, 0, 0, 0.464);
}

section {
    margin: 10%;
    background-color: rgb(193, 248, 248);
    padding: 12px;
}

header * {
    margin: 0;
}

button {
    background: transparent;
    border: none;
    font-weight: bolder;
    cursor: pointer;
    text-align: left;
    display: block;
    margin: 0 0 0 auto;
    padding: 3px;
}

button:hover {
    background-color: rgb(162, 227, 227);
}

</style>