<template>
    <div>
        <section>
            <button @click="changeFullDetails">Close</button>
            <header>
                <h1>{{film.title}} ({{film.release_date}})</h1>
                <h3>{{film.original_title_romanised}} - {{film.original_title}}</h3>
                <h4>{{film.running_time}} mins</h4>
            </header>
            <main>
                <p>Directed by: <span>{{film.director}}</span></p>
                <p>Produced by: <span>{{film.producer}}</span></p>
                <p>Rotten tomato score: <span>{{film.rt_score}}%</span></p>
                <p>{{film.description}}</p>
                <h4>Character list:</h4>
                <character-list :characters="film.people"/>
            </main>

        </section>
    </div>

</template>

<script>
import {eventBus} from '../main.js'
import CharacterList from './CharacterList.vue'

export default {
name: "film-full-details",
props: [
    "film",
    "characters"
],
methods: {
    changeFullDetails: function() {
        this.showFilmFull = false;
        eventBus.$emit("change-show-full-details", this.showFilmFull)
    }
},
components: {
    "character-list": CharacterList
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
    margin: 4% 5%;
    background-color: rgb(193, 248, 248);
    padding: 12px;
    overflow-y: scroll;
    height: 82%;
}

section * {
    margin: 0;
}

main {
    flex-direction: column;
    padding: 25px;
}

main * {
    margin-bottom: 10px;
}

span {
    font-weight: bold;
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
    color: rgb(144, 60, 60);
}

</style>