<template>
  <DataLoader url="https://jsonplaceholder.typicode.com/posts/1" />
</template>

<script>
import DataLoader from "./components/DataLoader";

export default {
  name: "App",
  components: {
    DataLoader,
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
