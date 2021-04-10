<template>
  <section>
      <h2>
        {{film.title}} - {{film.original_title}} ({{film.release_date}})
      </h2>
      <p>{{film.running_time}} mins</p>
      <p>{{film.description}}</p>
  </section>
</template>

<script>
export default {
name: 'film-details',
props: ["film"],

}
</script>

<style scoped>
    section{
        width: 55%;
        position: fixed;
        right: 50px;
        height: fit-content;
    }
</style>