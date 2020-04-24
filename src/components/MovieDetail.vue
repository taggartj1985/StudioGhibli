<template lang="html">
  <div>
   <h3>{{movie.title}}</h3>
   <p>Description: {{movie.description}}</p>
   <p>Rating: {{movie.rt_score}}</p>
 </div>
</template>

<script>
export default {
  name: 'movie-detail',
  props: ['movie']
}
</script>

<style lang="css" scoped>
</style>
