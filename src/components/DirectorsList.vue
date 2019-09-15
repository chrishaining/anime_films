<template lang="html">
  <div>
    <div>
      <director-item v-for="(director, id) in directorsList" v-bind:director-item="directorItem" v-bind:key="id"></director-item>

    </div>
    <!-- <label>Search for films by director</label>
    <select v-on:change="handleSelect" v-model="selectedDirector">
    <option value="" disabled selected>Select a director...</option>
    <option v-for="director in directors" :value="director">{{director.name}}</option>
  </select> -->

  <div>
    <label>Search for films by director</label>
    <select v-on:change="handleSelect" v-model="selectedDirector">
      <option value="" disabled selected>Select a director...</option>
      <option v-for="director in directorsList" :value="director">{{director}}</option>
    </select>
  </div>

</div>
</template>


<script>
import DirectorItem from './DirectorItem'
import {eventBus} from '../main'

export default {
  name: 'directors-list',
  data(){
    return {
      'search': "",
      'selectedDirector': {},
    }
  },
  methods: {
    handleSelect(){
      eventBus.$emit("director-selected", this.selectedDirector)
    },

    props: ['directors-list'],
    components: {'director-item': DirectorItem,
    'director': Director}
  }
}

</script>

<style lang="css" scoped>
</style>
