<template>
  <li>
      {{character.name}}
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

<style>

</style>