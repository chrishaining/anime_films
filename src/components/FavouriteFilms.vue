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
  display: flex;
  flex-direction: column;
  justify-content: space-around;
  border: solid black;
  margin: 1em;
}

li {
  padding: 0.2em;
  flex-direction: row;
  justify-content: flex-end;
}



</style>
