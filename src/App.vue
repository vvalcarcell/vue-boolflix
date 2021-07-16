<template>
  <div id="app">
    <Header @search="searchMovies" />
    <Main />
  </div>
</template>

<script>
import axios from "axios";
import Main from "./components/Main.vue";
import Header from "./components/Header.vue";

export default {
  name: "App",
  components: {
    Main,
    Header,
  },
  data() {
    return {
      moviesArray: [],
    };
  },
  methods: {
    searchMovies(inputText) {
      axios
        .get(
          "https://api.themoviedb.org/3/search/movie?api_key=852cb3344c4a5db3666052336469a824&query=" +
            inputText
        )
        .then((response) => {
          this.moviesArray = response.data.results;
        });
    },
  },
};
</script>

<style lang="scss">
</style>
