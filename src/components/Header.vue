<template>
  <div class="container">
    <nav>
      <img src="../assets/Netflix-logo.png" alt="" />
      <ul>
        <li><a href="#">Home</a></li>
        <li><a href="#">Serie Tv</a></li>
        <li><a href="#">Film</a></li>
        <li><a href="#">Originali</a></li>
        <li><a href="#">Aggiunti di recente</a></li>
        <li><a href="#">La mia lista</a></li>
      </ul>
    </nav>

    <!-- inputText viene inviato come argomento al method "searchMovies" per creare la API dinamica -->
    <div class="search-box">
      <input
        v-if="clickIcon"
        type="text"
        placeholder="Search..."
        v-model="inputText"
        @keyup.enter="$emit('search', inputText)"
        autofocus
      />
      <div
        class="search-icon"
        @click="
          $emit('search', inputText);
          getSearchBar();
        "
      >
        <i class="fas fa-search"></i>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Header",
  data() {
    return {
      inputText: "",
      clickIcon: false,
    };
  },
  methods: {
    getSearchBar() {
      if (this.clickIcon == false) {
        this.clickIcon = true;
      } else {
        this.inputText = "";
        this.clickIcon = false;
      }
    },
  },
};
</script>

<style lang="scss" scoped>
.container {
  padding: 25px 0;
  display: flex;
  justify-content: space-between;
  align-items: center;

  nav {
    display: flex;
    align-items: center;

    img {
      width: 150px;
      margin-right: 30px;
    }

    ul {
      display: flex;
      margin-top: 15px;
      font-size: 18px;

      a {
        margin-right: 18px;
        text-decoration: none;
        color: white;
      }
      /** quando vado su uno dei tag "a" l'underline compare a tutti... wtf!?! */
      //   &:hover {
      //     text-decoration: underline;
      //   }
    }
  }
  .search-box {
    display: flex;
    padding-top: 12px;
    padding-right: 15px;

    input[type="text"] {
      margin-right: 10px;
      padding: 3px;
      border-radius: 10px;
      border: 1px solid #ccc;
      font-weight: bold;

      &::placeholder {
        padding-left: 5px;
        font-weight: bold;
      }

      &:focus {
        outline: none;
      }
    }

    .search-icon {
      font-size: 25px;
      cursor: pointer;
    }
  }
}
</style>

