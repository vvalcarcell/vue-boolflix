<template>
  <div id="app">
    <Header @search="searchResults" />
    <Main
      :popularMovies="popularMovies"
      :filmsSearched="filmsSearched"
      :seriesSearched="seriesSearched"
      :filmsNotFound="filmsNotFound"
      :moviesNotFound="moviesNotFound"
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
      popularAPI:
        "https://api.themoviedb.org/3/movie/popular?api_key=852cb3344c4a5db3666052336469a824",
      filmsAPI:
        "https://api.themoviedb.org/3/search/movie?api_key=852cb3344c4a5db3666052336469a824&query=",
      seriesAPI:
        "https://api.themoviedb.org/3/search/tv?api_key=852cb3344c4a5db3666052336469a824&query=",
      filmsNotFound: false,
      moviesNotFound: false,
    };
  },
  /** Al caricamento della pagina faccio partire una chiamata per i film + popolari*/
  created() {
    axios.get(this.popularAPI).then((response) => {
      this.popularMovies = response.data.results;
    });
  },
  /** Chiamata dinamica verso film o serie tv in base alla ricerca dell'utente */
  methods: {
    searchResults(inputText) {
      if (inputText !== "") {
        axios.get(this.filmsAPI + inputText).then((response) => {
          this.filmsSearched = response.data.results;
          if (response.data.total_results == 0) {
            this.filmsNotFound = true;
          }
          console.log(response);
        });

        axios.get(this.seriesAPI + inputText).then((response) => {
          this.seriesSearched = response.data.results;
          if (response.data.total_results == 0) {
            this.moviesNotFound = true;
          }
        });
      } else {
        this.filmsSearched = [];
        this.seriesSearched = [];
        this.filmsNotFound = false;
        this.moviesNotFound = false;
      }
    },
  },
};
</script>

<style lang="scss">
@import url("./style/App.scss");
</style>