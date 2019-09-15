<template lang="html">
  <div id="main-container">
    <h1>Anime Films Catalogue</h1>
    <div id="lists-and-details">
      <films-list v-bind:films="films"></films-list>
      <film-details v-bind:film="selectedFilm"></film-details>
    <div>
      <favourite-films v-bind:favourite-films="favouriteFilms"></favourite-films>
    </div>
  </div>
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
h1 {
  background-color: #17E9C0;
  border: solid black;
  text-align: center;
}

#lists-and-details {
  background-color: white;
  border: solid black;
  /* display: inline; */

  /* justify-content: ; */
  /* align-items: flex-start;
  align-content: flex-start; */

}



</style>
