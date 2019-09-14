<template lang="html">
  <ul>
    <film-item v-for="(film, id) in favouriteFilms" v-bind:film="film" v-bind:key="id">
    </film-item>
  </ul>
</template>

<script>
import FilmItem from './FilmItem'

export default {
  name: 'favourite-films',
  props: ['favourite-films'],
  data(){
    return {
      "film": {}
    },
  components: {'film-item': FilmItem}
  }
  </script>

  <style lang="css" scoped>
  </style>
