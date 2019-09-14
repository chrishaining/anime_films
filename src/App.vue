<template lang="html">
  <div>
    <h1>Anime Films Catalog</h1>
    <films-list v-bind:films="films"></films-list>
    <film-details v-bind:film="selectedFilm"></film-details>
    <favourite-films v-bind:favourite-films="favouriteFilms"></favourite-films>

  </div>
</template>

<script>
import FilmsList from './components/FilmsList'
import FavouriteFilms from './components/FavouriteFilms' //not sure if this is possible
import FilmDetails from './components/FilmDetails'
import {eventBus} from './main'

export default {
  name: 'app',
  data() {
    return {
      films: [],
      selectedFilm: null,
      favouriteFilms: [] //is this the right place?
    }
  },
  // methods: {
  //   isBeerAFavourite: function(beer){
  //     const idsOfFavourites = (this.favourites.map(favourite => favourite.id))
  //     return idsOfFavourites.includes(beer.id)
  //   }
  // }
  methods: {
    markFavourite: function(film) {
      const idsOfFavouriteFilms = (this.favouriteFilms.map(favourite => favourite.id))
      if (!this.isFilmAFavourite(film)) this.favouriteFilms.push(film)
    },
    unmarkFavourite: function(film) {
      const index = this.favouriteFilms.indexOf(film);
      this.favouriteFilms.splice(index, 1)
    },
    isFilmAFavourite: function(film){
      const idsOfFavouriteFilms = (this.favouriteFilms.map(favourite => favourite.id))
      return idsOfFavouriteFilms.includes(film.id)

    },

    mounted() {
      fetch('https://ghibliapi.herokuapp.com/films')
      .then(result => result.json()) //is it already in json? If so, I won't need to do this step
      .then(films => this.films = films)

      eventBus.$on('film-selected', film => (this.selectedFilm = film));

      // eventBus.$on('favourite-film', (film) => {
      //   this.favouriteFilms.push(film);
      // })

      eventBus.$on('favourite-added', film => this.markFavourite(film));

      eventBus.$on('favourite-removed', film => this.unmarkFavourite(film));

    }


  },
  components: {
    'films-list': FilmsList,
    'film-details': FilmDetails,
    'favourite-films': FavouriteFilms //not sure if this is possible
  }
}


</script>

<style lang="css" scoped>
</style>
