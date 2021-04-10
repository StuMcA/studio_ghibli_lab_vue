<template>
  <section>
      <h2>
        {{film.title}} - {{film.original_title}} ({{film.release_date}})
      </h2>
      <p>{{film.running_time}} mins</p>
      <p>{{description}}</p>
      <div>Click for more</div>
  </section>
</template>

<script>
export default {
name: 'film-details',
props: [
    "film",
    "description"
],

methods: {

},
mounted() {
    this.shortenDescription(this.film)
}
}
</script>

<style scoped>
    section{
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