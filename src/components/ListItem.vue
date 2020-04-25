<template lang="html">
<div  class="list">
<ul>
  <li v-on:click="handleClick">{{movie.title}}</li>
</ul>

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
.list{
  font-size: 25px;
  font-weight: bold;
  color: black;
  text-align: center;
}
ul {
   display: flex;
   flex-direction: column;
   flex-wrap: wrap;
   width: 100%;
   padding-left: 0;
 }



</style>
