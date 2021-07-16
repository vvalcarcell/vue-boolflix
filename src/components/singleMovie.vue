<template>
  <div class="single-movie">
    <img
      src="https://image.tmdb.org/t/p/w342/hQq8xZe5uLjFzSBt4LanNP7SQjl.jpg"
      alt=""
    />

    <div class="info-movie">
      <h3>{{ movie.title }}</h3>
      <div class="info">Original Title: {{ movie.original_title }}</div>
      <div class="info">Original Language: {{ movie.original_language }}</div>
      <div class="info">Vote-average: {{ movie.vote_average }}</div>
    </div>
  </div>
</template>

<script>
export default {
  name: "singleMovie",
  props: {
    movie: Object,
  },
};
</script>

<style lang="scss" scoped>
.single-movie {
  position: relative;
  margin-left: 10px;
  margin-bottom: 20px;

  &:hover .info-movie {
    display: block;
  }

  .info-movie {
    text-transform: capitalize;
    position: absolute;
    top: 70%;
    left: 20px;
    z-index: 1001;
    color: white;
    display: none;
  }
}
</style>