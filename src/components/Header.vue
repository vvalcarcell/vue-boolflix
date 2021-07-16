<template>
  <div class="container">
    <input
      type="text"
      placeholder="Search"
      v-model="inputText"
      @keyup.enter="$emit('search', inputText)"
    />
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
</style>

