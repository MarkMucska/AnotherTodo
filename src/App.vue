<template>
  <div id="app" class="container">
    <img alt="Vue logo" src="./assets/logoM.png" class="logo"/>
    <userInput class="user-input" msg="Welcome to Your Vue.js App" />
  </div>
</template>

<script>
import userInput from "./components/userInput.vue";

export default {
  name: "App",
  components: {
    userInput
  }
};
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 20px;
}
.container {
  max-width: 600px;
  margin: 0 auto;
}
.logo {
  width: 100px;
}
</style>
