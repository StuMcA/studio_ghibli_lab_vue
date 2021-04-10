<template>
  <li>
    <p>{{film.title}}</p>
  </li>
</template>

<script>
export default {
name:'film-item',
props: [
  'film'
]
}
</script>

<style scoped>

li {
  list-style: none;
}
</style>>

</style>