<template>
  <div id="app">
    <user-rating></user-rating>
  </div>
</template>

<script>
import UserRating from "./components/UserRating.vue";

export default {
  name: "App",
  components: {
    UserRating,
  },
};
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
