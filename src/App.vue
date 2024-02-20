<template>
  <div id="app">
    <h1>Movies ({{ totalMovies }})</h1>
    <ul>
      <movie-item
        v-for="movie in movies"
        :key="movie.id"
        :title="movie.title"
        :year="movie.year"
      ></movie-item>
    </ul>

    <input type="text" v-model="newMovieTitle" placeholder="Enter movie title">
    <input type="number" v-model.number="newMovieYear" placeholder="Enter release year">
    <button @click="addMovie">Add Movie</button>
  </div>
</template>

<script>
import MovieItem from './components/MovieItem.vue'; 

export default {
  name: 'App',
  components: {
    MovieItem, 
  },
  data() {
    return {
      movies: [],
      newMovieTitle: '',
      newMovieYear: null
    };
  },
  computed: {
    totalMovies() {
      return this.movies.length;
    }
  },
  methods: {
    addMovie() {
      if (this.newMovieTitle && this.newMovieYear) {
        this.movies.push({
          id: this.movies.length + 1,
          title: this.newMovieTitle,
          year: this.newMovieYear
        });
        this.newMovieTitle = '';
        this.newMovieYear = null;
      }
    }
  },
  mounted() {
    console.log('Vue app mounted');
  }
};
</script>


<style>
body {
  font-family: Arial, sans-serif;
  background-color: #000;
  color: #fff;
}

#app {
  max-width: 600px;
  margin: 0 auto;
  padding: 20px;
}

h1 {
  color: #ff0000;
}

input[type="text"],
input[type="number"],
button {
  display: block;
  margin-bottom: 10px;
  padding: 8px;
  width: 100%;
  border: 1px solid #ff0000;
  background-color: #000;
  color: #fff;
}

input[type="text"]::placeholder,
input[type="number"]::placeholder {
  color: #888;
}

button {
  cursor: pointer;
  background-color: #ff0000;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  margin-bottom: 10px;
  padding: 10px;
  background-color: #333;
  border-radius: 5px;
}

li:hover {
  background-color: #444;
}

</style>
