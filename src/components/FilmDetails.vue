<template lang="html">
  <div class="details" v-if="film">
    <p>{{film.title}}</p>
    <p>{{film.director}}</p>
    <p>{{film.description}}</p>
    <!-- <p>{{film.people}}</p> -->
    <!-- <button v-if="!favouriteFilms.includes(film)" v-on:click="addToFavourites"> Add to favourites </button> -->

    <button v-if="!isFavourite" v-on:click="addFavourite">
      Add to Favourites</button>
    <button v-if="isFavourite" v-on:click="removeFavourite">
      Remove from Favourites</button>

    <!-- could also add a line to show whether if it is a favourite - v-if="favouriteFilms.includes(film)" <p>This is on your favourites list</p> <button v-if="favouriteFilms.includes(film)" v-on:click="RemoveFromFavourites">Remove from favourites</button>-->

  </div>
</template>

<script>
export default {
  name: 'film-details',
  props: ['film', 'isFavourite'],
  methods: {
    // addToFavourites: function() {
    //   eventBus.$emit("favourite-film", this.film)
    // },
    // removeFromFavourites: function() {
    //   eventBus.$emit("")

      addFavourite: function() {
       eventBus.$emit('favourite-added', this.film);
     },

     removeFavourite: function() {
       eventBus.$emit('favourite-removed', this.film);
     }

    
  }
}
</script>

<style lang="css" scoped>
  .details {
    background-color: beige;
  }
</style>
