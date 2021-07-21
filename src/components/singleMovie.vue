<template>
  <div
    class="single-movie"
    :style="'background-image:url(' + completeSrc(movie.poster_path) + ')'"
  >
    <div class="info-movie">
      <!-- a seconda l'oggetto sia un film o una serie tv -->
      <h3>{{ movie.title }} {{ movie.name }}</h3>
      <div class="info">
        Original Title: {{ movie.original_title }} {{ movie.original_name }}
      </div>
      <div class="info">Original Language: {{ movie.original_language }}</div>
      <div class="info">
        Nation:
        <img class="flag" :src="returnFlag(movie.original_language)" alt="" />
      </div>

      <ul>
        <li v-for="(n, index) in vote" :key="index">
          <i class="fas fa-star"></i>
        </li>

        <li v-for="(num, index) in emptyStars" :key="'A' + index">
          <i class="far fa-star"></i>
        </li>
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
      emptyStars: 5 - Math.round(this.movie.vote_average / 2),
    };
  },
  methods: {
    completeSrc(partialSrc) {
      return "https://image.tmdb.org/t/p/w342" + partialSrc;
    },
    /** Mettendo il bind ad src, senza il method "require" non mi prende l'svg(tratta assets come un modulo?) */
    returnFlag(originalLanguage) {
      return require("../assets/flags/" + originalLanguage + ".svg");
    },
  },
};
</script>

<style lang="scss" scoped>
.single-movie {
  position: relative;
  margin-right: 10px;
  margin-bottom: 20px;
  background-size: cover;
  height: 510px;
  width: 340px;
  flex-shrink: 0;
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
    .flag {
      width: 20px;
      margin-top: 5px;
    }
    ul {
      display: flex;
      margin-top: 5px;
    }
  }
  .background {
    height: 100%;
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