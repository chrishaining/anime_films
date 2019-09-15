<template lang="html">
  <ul>
    <label>Select a film : </label>
    <film-item v-for="(film, index) in films" v-bind:film="film" v-bind:key="index"></film-item>
  </ul>
</template>

<script>
import FilmItem from './FilmItem'

export default {
  name: 'films-list',
  props: ['films'],
  components: {'film-item': FilmItem},


}
</script>

<style lang="css" scoped>
</style>
