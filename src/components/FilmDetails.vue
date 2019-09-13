<template lang="html">
  <div class="details" v-if="film">
  <p>{{film.title}}</p>
  <p>{{film.director}}</p>
  <p>{{film.description}}</p>
  <p>{{film.people}}</p>
  </div>
</template>

<script>
export default {
  name: 'film-details',
  props: ['film']
}
</script>

<style lang="css" scoped>
.details {
  background-color: beige;
}
</style>
