<template lang="html">
  <div>
<ul class="list">
    <list-item v-for="(movie, index) in movies" :movie="movie"  :key="index"> </list-item>
</ul>
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
