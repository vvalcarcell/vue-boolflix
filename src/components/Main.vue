<template>
  <div class="container">
    <h1>I più popolari</h1>
    <div class="row-popular">
      <!-- Creo tanti components "singleMovie" quanti sono gli elementi di moviesArray -->
      <!-- Invio al component "singleMovie" il singolo oggetto contenuto in moviesArray -->
      <singleMovie
        v-for="movie in moviesArray"
        :key="movie.id"
        :movie="movie"
      />
    </div>
  </div>
</template>

<script>
import singleMovie from "./singleMovie.vue";
export default {
  name: "Main",
  props: {
    moviesArray: Array,
  },
  components: {
    singleMovie,
  },
};
</script>

<style lang="scss" scoped>
.row-popular {
  display: flex;
  overflow-x: scroll;
}
</style>