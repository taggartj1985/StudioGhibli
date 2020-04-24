<template lang="html">
  <div>
   <h2>{{movie.title}}</h2>
   <p>Description: {{movie.description}}</p>
   <p>Rating: {{movie.rt_score}}</p>
   <p>Director: {{movie.director}}</p>
   <p>Release Date: {{movie.release_date}}</p>
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
