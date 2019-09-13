<template lang="html">
  <div v-if="film">
  <p>{{film.title}}</p>
  <p>{{film.id}}</p>
  </div>
</template>

<script>
export default {
  name: 'film-details',
  props: ['film']
}
</script>

<style lang="css" scoped>
</style>
