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
import FilmDetails from './components/FilmDetails'
import FavouriteFilms from './components/FavouriteFilms'

import {eventBus} from './main'

export default {
  name: 'app',
  data() {
    return {
      films: [],
      selectedFilm: null,
      favouriteFilms: []
    }
  },

  mounted() {
    fetch('https://ghibliapi.herokuapp.com/films')
    .then(result => result.json()) //is it already in json? If so, I won't need to do this step
    .then(films => this.films = films)

    eventBus.$on('film-selected', (film) => {
      this.selectedFilm = film
    })
    // addToFavourites
    eventBus.$on('favourite-films-item', (film) => {
      if (!this.favouriteFilms.includes(film)) {
        this.favouriteFilms.push(film);
      }
    })

    //removeFromFavourites
    eventBus.$on('favourite-removed', (film) => {
      const index = this.favouriteFilms.indexOf(film);
      this.favouriteFilms.splice(index, 1)
    })

  },
  components: {
    'films-list': FilmsList,
    'film-details': FilmDetails,
    'favourite-films': FavouriteFilms

  }
}


</script>

<style lang="css" scoped>
</style>
