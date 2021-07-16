<template>
  <div class="single-movie">
    <img :src="completeSrc(movie.poster_path)" alt="" />

    <div class="info-movie">
      <h3>{{ movie.title }}</h3>
      <div class="info">Original Title: {{ movie.original_title }}</div>
      <div class="info">Original Language: {{ movie.original_language }}</div>
      <div class="info">Vote-average: {{ movie.vote_average }}</div>
    </div>

    <div class="background"></div>
  </div>
</template>

<script>
export default {
  name: "singleMovie",
  props: {
    movie: Object,
  },
  methods: {
    completeSrc(partialSrc) {
      return "https://image.tmdb.org/t/p/w342" + partialSrc;
    },
  },
};
</script>

<style lang="scss" scoped>
.single-movie {
  position: relative;
  margin-right: 10px;
  margin-bottom: 20px;

  &:hover .info-movie {
    display: block;
  }

  &:hover .background {
    display: block;
  }

  .info-movie {
    text-transform: capitalize;
    position: absolute;
    top: 30%;
    left: 20px;
    z-index: 1002;
    color: white;
    display: none;
  }

  .background {
    height: calc(100% - 5px);
    width: 100%;
    position: absolute;
    top: 0;
    left: 0;
    background-color: rgba(0, 0, 0, 0.486);
    z-index: 1001;
    display: none;
  }
}
</style>