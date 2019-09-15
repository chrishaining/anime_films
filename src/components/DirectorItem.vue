<template lang="html">
  <div>
    <!-- <director v-bind:director="director"></director> -->
    <li v-on:click="handleDirectorClick">{{director}}</li>

  </div>
</template>

<script>
import { eventBus } from '../main.js'

export default {
  name: 'director-item',
  props: ['director-item'],
  methods: {
    handleDirectorClick() {
      eventBus.$emit('director-selected', this.director)
    }
  }
  // components: {'director': Director}
}

</script>

<style lang="css" scoped>
</style>
