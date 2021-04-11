<template>
  <li>
      <span>{{character.name}}</span> ({{character.species.name}})
  </li>
</template>

<script>
export default {
name: 'character-item',
props: [
    'character'
]
}
</script>

<style scoped>
span {
    font-weight: bold;
}

</style>