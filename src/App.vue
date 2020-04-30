<template>
  <div id="app">
    <Home />
  </div>
</template>

<script>
import Home from "@/components/Home.vue";

export default {
  name: "App",
  components: {
    Home
  }
};
</script>

<style>
@import url("https://fonts.googleapis.com/css2?family=Open+Sans+Condensed:wght@700&display=swap");
#app {
  font-family: "Open Sans Condensed", sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  background: #ca95ca;
  display: grid;
  height: 95vh;
  align-items: center;
  justify-items: center;
}
</style>
