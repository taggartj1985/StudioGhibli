<template>
  <div id="app">
    <section id="header">
  <img src="logo.png" alt="totoro">
    <h1>Movie List</h1>
      </section>
      <section id="list">
    <movie-list :movies='movies'></movie-list>
      </section>
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
    .then(data => this.movies = data),

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
  color: #2c3e50;
  margin-top: 60px;
}

#header{
  background-color:  #40bad5;
  text-align: center;
}

#list{ display: inline-block; }

</style>
