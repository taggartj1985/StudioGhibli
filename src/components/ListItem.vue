<template lang="html">
<div >

  <li v-on:click="handleClick">{{movie.title}}</li>

  </div>
</template>

<script>
import {eventBus} from '../main.js'

export default {
  name: 'list-item',
  props: ['movie'],
  methods: {
  handleClick(){
    eventBus.$emit('movie-selected', this.movie)
  }
}
}
</script>

<style lang="css" scoped>
</style>
