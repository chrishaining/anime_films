<template lang="html">
  <ul>
    <film-item v-for="(film, id) in films" v-bind:film="film" v-bind:key="id"></film-item>
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
