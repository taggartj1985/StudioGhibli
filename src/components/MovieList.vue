<template lang="html">
  <div>
    <list-item v-for="(movie, index) in movies" :movie="movie"  :key="index"> </list-item>
</div>
</template>

<script>
import ListItem from './ListItem.vue';
export default {
  name: 'movie-list',
  props: ['movies'],
  components: {
    "list-item": ListItem
  }
}
</script>

</style>
