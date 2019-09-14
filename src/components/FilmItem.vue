<template lang="html">
  <div>
  <li v-on:click="handleClick">{{film.title}}</li>

<!-- :isFavourite="$parent.isBeerAFavourite(beer)" a prop in details.  i could put this in the films list, by putting it inside the v-for. would mean the v-for should be moved outside the ul and into a div container, or kept inside the ul and put into li tags. -->

</div>
</template>

<script>
import { eventBus } from '../main.js'

export default {
  name: 'film-item',
  props: ['film'],
  methods: {
    handleClick() {
      eventBus.$emit('film-selected', this.film)
    },


  }
}

</script>

<style lang="css" scoped>
</style>
