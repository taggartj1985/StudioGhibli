<template>
  <div id="app">
    <h1>Studio Ghibli</h1>
    <movie-list :movies='movies'></movie-list>
    <movie-detail v-if="selectedMovie" :movie="selectedMovie"></movie-detail>
  </div>
</template>

<script>
import MovieList from './components/MovieList.vue';
import {eventBus} from './main.js';
import  MovieDetail from './components/MovieDetail.vue';


export default {
  name: 'App',
  data(){
    return {
      movies: [],
      selectedMovie: null,
    };
  },
  mounted(){
    fetch('https://ghibliapi.herokuapp.com/films')
    .then(res => res.json())
    .then(data => this.movies = data);

    eventBus.$on('movie-selected', (movie) => {
    this.selectedMovie = movie;
  })
  },
  components: {
    "movie-list": MovieList,
    "movie-detail": MovieDetail
  }

}

</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
