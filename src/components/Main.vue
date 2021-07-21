<template>
  <div class="container">
    <div class="films-container" v-if="filmsSearched.length != 0">
      <h1>Film</h1>
      <div class="row">
        <singleMovie
          v-for="movie in filmsSearched"
          :key="movie.id"
          :movie="movie"
        />
      </div>
    </div>

    <div class="series-container" v-if="seriesSearched.length != 0">
      <h1>Serie tv</h1>
      <div class="row">
        <singleMovie
          v-for="movie in seriesSearched"
          :key="movie.id"
          :movie="movie"
        />
      </div>
    </div>

    <div class="popular-container">
      <h1>I più popolari</h1>
      <div class="row">
        <!-- Creo tanti components "singleMovie" quanti sono gli elementi di moviesArray -->
        <!-- Invio al component "singleMovie" il singolo oggetto contenuto in moviesArray -->
        <singleMovie
          v-for="movie in popularMovies"
          :key="movie.id"
          :movie="movie"
        />
      </div>
    </div>
  </div>
</template>

<script>
import singleMovie from "./singleMovie.vue";
export default {
  name: "Main",
  props: {
    popularMovies: Array,
    filmsSearched: Array,
    seriesSearched: Array,
  },
  components: {
    singleMovie,
  },
};
</script>

<style lang="scss" scoped>
.row {
  display: flex;
  overflow-x: scroll;
}
</style>