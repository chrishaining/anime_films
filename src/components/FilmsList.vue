<template lang="html">
  <ul>
    <label>Click a film: </label>
    <film-item v-for="(film, index) in films" v-bind:film="film" v-bind:key="index"></film-item>
  </ul>
</template>

<script>
import FilmItem from './FilmItem'

export default {
  name: 'films-list',
  props: ['films'],
  components: {'film-item': FilmItem},
  data(){
    return {
      "selectedFilm": {}
    }
  }
}
</script>

<style lang="css" scoped>

ul {
  list-style: none;
  background-color: #FFB48F;
  padding: 0.5em;
  width: 40%;
  margin: 1em;
  border: 0.2em solid black;
}

li:hover {
  background: #17E9C0; ;
}

li:active {
  background: #095d59;
}


</style>
