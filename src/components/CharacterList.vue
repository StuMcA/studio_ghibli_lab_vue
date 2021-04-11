<template>
  <ul>
        <character-item v-for="(character, id) in characters" :key="id" :character="character" />
  </ul>
</template>

<script>
import CharacterItem from './CharacterItem.vue'

export default {
name: "character-list",
props: [
    "characters"
],
components: {
  'character-item': CharacterItem
}
}
</script>

<style>

</style>