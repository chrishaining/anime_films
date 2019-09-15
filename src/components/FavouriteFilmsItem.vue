<template lang="html">
  <!-- <li v-on:click="handleClick">{{film.title}}</li> -->
    <!-- <li v-if"favouriteFilmsItem">{{film.title}}</li> -->

</template>

<script>
import { eventBus } from '../main.js'
import FavouriteFilms from './FavouriteFilms'

export default {
  name: 'favourite-films-item',
  props: ['favourite-films-item', 'film']
  // methods: {
  //   handleClick() {
  //     eventBus.$emit('film-selected', this.film)
    // }
  // }
}

</script>

<style lang="css" scoped>
</style>
