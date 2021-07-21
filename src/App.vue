<template>
  <div id="app">
    <Header @search="searchMovies" />
    <Main
      :popularMovies="popularMovies"
      :filmsSearched="filmsSearched"
      :seriesSearched="seriesSearched"
    />
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
      /** lista che verrà stampata */
      popularMovies: [],
      filmsSearched: [],
      seriesSearched: [],
    };
  },
  /** Al caricamento della pagina faccio partire una chiamata per i film + popolari*/
  created() {
    axios
      .get(
        "https://api.themoviedb.org/3/movie/popular?api_key=852cb3344c4a5db3666052336469a824"
      )
      .then((response) => {
        this.moviesArray = response.data.results;
        this.popularMovies = response.data.results;
      });
  },
  /** Chiamata dinamica verso film o serie tv in base alla ricerca dell'utente */
  methods: {
    searchMovies(inputText) {
      if (inputText !== "") {
        axios
          .get(
            "https://api.themoviedb.org/3/search/movie?api_key=852cb3344c4a5db3666052336469a824&query=" +
              inputText
          )
          .then((response) => {
            this.filmsSearched = response.data.results;
          });

        axios
          .get(
            "https://api.themoviedb.org/3/search/tv?api_key=852cb3344c4a5db3666052336469a824&query=" +
              inputText
          )
          .then((response) => {
            this.seriesSearched = response.data.results;
          });
      } else {
        this.filmsSearched = [];
        this.seriesSearched = [];
      }
    },
  },
};
</script>

<style lang="scss">
@import url("./style/App.scss");
</style>