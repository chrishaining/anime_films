<template lang="html">

  <ul>
    <label>Favourite Films</label>
    <!-- <favourite-films-item v-for="(film, id) in favouriteFilms" v-bind:favourite-films-item="favouriteFilmsItem" v-bind:key="id"></favourite-films-item> -->
      <li v-for="film in favouriteFilms" :value="film">{{film.title}}</li>
  </ul>

</template>

<script>
import FavouriteFilmsItem from './FavouriteFilmsItem'

export default {
  name: 'favourite-films',
  // data(){
  //   return {
  //     "favouriteFilm": {}
  //   }
  // },

  props: ['favourite-films'],
  components: {'favourite-films-item': FavouriteFilmsItem},


}
</script>

<style lang="css" scoped>
</style>
