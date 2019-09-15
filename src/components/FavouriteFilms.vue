<template lang="html">

  <ul>
    <label>Favourite Films</label>
    <li v-for="film in favouriteFilms" :value="film">{{film.title}}
<button v-on:click="removeFromFavouriteFilms">Remove from Favourites</button>
    </li>
  </ul>

</template>

<script>
import FavouriteFilmsItem from './FavouriteFilmsItem'
import { eventBus } from '../main.js'

export default {
  name: 'favourite-films',
  methods: {
    removeFromFavouriteFilms: function() {
      eventBus.$emit("favourite-removed", this.film)
    }
  },
  props: ['favourite-films'],
  components: {'favourite-films-item': FavouriteFilmsItem},
}
</script>

<style lang="css" scoped>
ul {
  list-style: none;
  background-color: #A64AC9;
  padding: 0.5em;
}
</style>
