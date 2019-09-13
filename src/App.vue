<template lang="html">
  <div>
    <h1>Anime Films Catalog</h1>
    <films-list v-bind:films="films"></films-list>
    <film-details v-bind:film="selectedFilm"></film-details>
  </div>
</template>

<script>
import FilmsList from './components/FilmsList'
import FilmDetails from './components/FilmDetails'
import {eventBus} from './main'

export default {
  name: 'app',
  data() {
    return {
      films: [],
      selectedFilm: null
    }
  },

  mounted() {
    fetch('https://ghibliapi.herokuapp.com/films')
    .then(result => result.json()) //is it already in json? If so, I won't need to do this step
    .then(films => this.films = films)

    eventBus.$on('film-selected', (film) => {
      this.selectedFilm = film
    })

  },
  components: {
    'films-list': FilmsList,
    'film-details': FilmDetails
  }
}


</script>

<style lang="css" scoped>
</style>
