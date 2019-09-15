<template lang="html">
  <div class="details" v-if="film">
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
  background-color: #FCCD04;
  padding: 0.5em;
}
</style>
