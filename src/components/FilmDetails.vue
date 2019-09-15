<template lang="html">
  <div class="details" v-if="film">
    <h1>Film details</h1>
    <p>Title: {{film.title}}</p>
    <p>Director: {{film.director}}</p>
    <p>Description: {{film.description}}</p>
    <button v-on:click="addToFavourites"> Add to favourites </button>
  </div>
</template>

<script>

import FavouriteFilms from './FavouriteFilms'
import { eventBus } from '../main'

export default {
  name: 'film-details',
  props: ['film', 'favourite-films-item'],
  methods: {
    addToFavourites: function() {
      eventBus.$emit("favourite-films-item", this.film)
    }

  }
}
</script>

<style lang="css" scoped>
.details {
  margin: 1em;
  float: right;
  background-color: #FCCD04;
  padding: 0.5em;
  text-align: center;
  border: solid black;

}
</style>
