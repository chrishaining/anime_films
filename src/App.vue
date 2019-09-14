<template lang="html">
  <div>
    <h1>Anime Films Catalog</h1>


    <div>
      <films-list v-bind:films="films"></films-list>
      <film-details v-bind:film="selectedFilm"></film-details>
    </div>
    <div>
      <directors-list v-bind:directors-list="directorsList"></directors-list>
      <director v-bind:director="selectedDirector"></director>


      <!-- <form v-on:submit.prevent> -->
      <!-- <label>Search for films by director</label> -->
      <!-- <input type="text" v-model="search" placeholder="search for a director" v-on:keyup="findAllFilmsByDirector">
      <director v-bind:director="director"></director> -->

      <!-- <input type="text" v-model="director"> -->
      <!-- <director v-bind:director="director"></director>
      <input type="text">

      <datalist>
      <option v-for="film in films">{{film.director}}</option>
    </datalist>
    <button v-on:click="findAllFilmsByDirector">Submit</button> -->

  </div>

  <!-- <select v-on:change="handleSelect" v-model="selectedDirector">
  <option disabled value="">Select a director...</option>
  <option v-for="(film, director) in films" :value="director">{{film.director}}</option>
</select> -->
<!-- </form> -->
</div>

</template>

<script>
import FilmsList from './components/FilmsList'
import FilmDetails from './components/FilmDetails'
import DirectorsList from './components/DirectorsList'
import DirectorItem from './components/DirectorItem'
import Director from './components/Director'
import {eventBus} from './main'

export default {
  name: 'app',
  data() {
    return {
      films: [],
      selectedFilm: null,
      directorsList: [],
      selectedDirector: null
    }
  },
  methods: {
    findAllFilmsByDirector: function(director){
      return this.films.filter(film => film.director === director)
    }

  },

  mounted() {
    fetch('https://ghibliapi.herokuapp.com/films')
    .then(result => result.json()) //is it already in json? If so, I won't need to do this step
    .then(films => this.films = films)

    eventBus.$on('film-selected', (film) => {
      this.selectedFilm = film
    })

    eventBus.$on('director-selected', (director) => {
      this.selectedDirector = director
    })

  },
  components: {
    'films-list': FilmsList,
    'film-details': FilmDetails,
    'directors-list': DirectorsList,
    'director': Director
  }
}


</script>

<style lang="css" scoped>
</style>
