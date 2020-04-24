<template>
  <div id="white">
  <div id="app" :style="{'background-image':'url(totoros.jpg)'}">
    <section id="header">
  <img src="logo.png" alt="totoro">
    <h1>Movie List</h1>
  </section>
      <section id="list">
    <movie-list :movies='movies'></movie-list>
      </section>

    <movie-detail id="movie-list" v-if="selectedMovie" :movie="selectedMovie"></movie-detail>
    <button v-if="!watchedMovies.includes(selectedMovie)" v-on:click="addToWatched">Watched</button>
      </div>
      <!-- <canvas id="canvas" width="100%" height="100%"></canvas> -->
      <div id="watched-movies">
      <h1>Watched Movies</h1>
        <li v-for="watchedMovie in watchedMovies">{{watchedMovie.title}}</li>
      </div>
    </div>
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
      watchedMovies: [],
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
  },

  methods: {
      addToWatched: function(){
        this.watchedMovies.push(this.selectedMovie)
      },
    }
}

</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  margin-top: 0px;
}

#header{
  background-color:  #40bad5;
  text-align: center;
  color: black;
}

#list{
  font-size: 25px;
  font-weight: bold;
  color: black;
  margin: 20;
}

#movie-list{
  font-size: 20px;
  font-weight: bold;
  color: black;
}

#white{
  background: white;
  opacity: 0.85;
}

#canvas{ border: 1px solid black;
background: red;}

</style>
