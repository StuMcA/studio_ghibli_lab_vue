<template>
  <ul>
        <character-item v-for="(character, id) in characters" :key="id" :character="character" />
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