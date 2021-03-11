<template>
  <img alt="star war logo" src="./assets/star-wars.jpg" />
  <DataDisplay />
</template>

<script>
import DataDisplay from "./components/StarWars/DataDisplay";

export default {
  name: "App",
  components: {
    DataDisplay
  }
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
img {
  width: 200px;
  height: 100px;
}
</style>
