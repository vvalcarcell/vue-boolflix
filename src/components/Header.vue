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

    <div class="search-box">
      <input
        type="text"
        placeholder="Search"
        v-model="inputText"
        @keyup.enter="$emit('search', inputText)"
      />
      <button @click="$emit('search', inputText)">Search</button>
    </div>
  </div>
</template>

<script>
export default {
  name: "Header",
  data() {
    return {
      inputText: "",
    };
  },
};
</script>

<style lang="scss" scoped>
.container {
  padding: 25px;
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
      list-style: none;
      display: flex;
      margin-top: 15px;
      font-size: 15px;

      a {
        margin-right: 18px;
        text-decoration: none;
        color: white;
      }

      //   &:hover {
      //     text-decoration: underline;
      //   }
    }
  }
  .search-box {
    margin-right: 10px;

    input {
      margin-right: 10px;
    }
  }
}
</style>

