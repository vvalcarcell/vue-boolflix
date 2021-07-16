<template>
  <div class="container">
    <input
      type="text"
      placeholder="Search"
      v-model="inputText"
      @keyup.enter="$emit('search', inputText)"
    />
    <button @click="$emit('search', inputText)">Search</button>
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
  height: 100px;
  display: flex;
  align-items: center;
}
</style>

