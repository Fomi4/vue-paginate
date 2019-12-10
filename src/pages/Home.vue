<template lang="html">
  <div>
    <h1>Hello world</h1>

    Search: <input type="text" v-model="query" value="">
    <button @click="search" type="button">Search</button>

    <p>Page {{ page }}</p>
    <button @click="nextPage" type="button" :disabled="lastPage">Next Page</button>
    <MovieList :movies="movies" />
  </div>
</template>

<script>
import MovieList from '../components/MovieList';

export default {
  name: 'Home',
  components: {
    MovieList
  },
  data: () => ({
    query: '',
    // lastPage: false,
    maxPage: 1,
    page: 1,
    movies: [],
  }),
  methods: {
    search() {
      fetch(`https://api.themoviedb.org/3/search/movie?query=${this.query}&page=${this.page}&api_key=e55aedd9c2529e025021dda202c18d3b`)
        .then(response => response.json())
        .then(data => {
          this.maxPage = data.total_pages;
          this.movies = data.results.map(x => ({
            id: x.id,
            title: x.title,
            releaseData: x.release_data,
            language: x.original_language
          }))
        })
    },
    nextPage() {
      // if (this.page + 1 === this.maxPage) this.lastPage = true;
      this.page++;
      this.search();
    }
  },
  computed: {
    lastPage() {
      return this.page === this.maxPage;
    }
  }
}
</script>

<style lang="css" scoped>
</style>
