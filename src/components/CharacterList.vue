<template>
  <ul>
      <li v-for="(character) in characters">
          <character-item />
      </li>
  </ul>
</template>

<script>
export default {
name: "character-list",
props: [
    "characters"
]
}
</script>

<style>

</style>