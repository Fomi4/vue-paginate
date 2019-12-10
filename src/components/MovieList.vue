<template lang="html">
  <div>
    <div v-for="movie in movies" :key="movie.id">
      <Movie
        :id="movie.id"
        :title="movie.title"
        :releaseDate="movie.releaseDate"
        :language="movie.language"
      />
    </div>
  </div>
</template>

<script>
import Movie from './Movie'

export default {
  name: 'MovieList',
  props: {
    movies: Array
  },
  components: {
    Movie
  },
}
</script>

<style lang="css" scoped>
</style>
