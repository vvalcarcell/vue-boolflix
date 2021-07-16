<template>
  <div class="single-movie">
    <!-- inviando "movie.poster_path" come argomento del method, mi ritorna l'src completo -->
    <img :src="completeSrc(movie.poster_path)" alt="" />

    <div class="info-movie">
      <!-- a seconda l'oggetto sia un film o una serie tv -->
      <h3>{{ movie.title }} {{ movie.name }}</h3>
      <div class="info">
        Original Title: {{ movie.original_title }} {{ movie.original_name }}
      </div>
      <div class="info">Original Language: {{ movie.original_language }}</div>

      <ul v-if="vote > 0">
        <li><i class="far fa-star"></i></li>
        <li v-if="vote > 1"><i class="far fa-star"></i></li>
        <li v-if="vote > 2"><i class="far fa-star"></i></li>
        <li v-if="vote > 3"><i class="far fa-star"></i></li>
        <li v-if="vote > 4"><i class="far fa-star"></i></li>
      </ul>
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
  data() {
    return {
      // arrotondo la media dei voti all'intero più vicino e divido per 2 per utilizzare solo 5 stelle intere
      vote: Math.round(this.movie.vote_average / 2),
    };
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

    h3 {
      margin-bottom: 15px;
    }

    .info {
      margin-bottom: 5px;
    }

    ul {
      display: flex;
      margin-top: 5px;
    }
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