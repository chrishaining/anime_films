<template lang="html">
  <div>
    <h1>WEEEEEEEEEE!!!</h1>
    <films-list></films-list>
    <film-details></film-details>
  </div>
</template>

<script>
import FilmsList from './components/FilmsList'
import FilmDetail from './components/FilmDetail'
import {eventBus} from './main'

export default {
  name: 'app',
  data() {
    films: [],
    selectedFilm: null
  },

  mounted() {
    fetch'(https://ghibliapi.herokuapp.com/films')
      .then(result => result.json()) //is it already in json? If so, I won't need to do this step
      .then(films => films = this.films)
    },
    components: {
      'films-list': FilmsList,
      'film-detail': FilmDetail
    }
}

    </script>

    <style lang="css" scoped>
    </style>
