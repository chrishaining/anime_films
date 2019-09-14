<template lang="html">
  <div class="details" v-if="director">

    <p v-for="director in directors">{{findAllFilmsByDirector(director)}}</p>
  </div>
</template>

<script>
import { eventBus } from '../main'
import DirectorsList from './DirectorsList'
import FilmsList from './FilmsList'


export default {
  name: 'director',
  props: ['director'],
  methods: {
    findAllFilmsByDirector: function(director){
      return this.films.filter(film => film.director === director)
    }

  }
}

</script>

<style lang="css" scoped>
.details {
  background-color: dodgerblue;
}
</style>
