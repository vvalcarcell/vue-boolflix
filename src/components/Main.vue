<template>
  <div class="container">
    <!-- Creo tanti components "singleMovie" quanti sono gli elementi di moviesArray -->
    <!-- Invio al component "singleMovie" il singolo oggetto contenuto in moviesArray -->
    <singleMovie v-for="movie in moviesArray" :key="movie.id" :movie="movie" />
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
.container {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
}
</style>