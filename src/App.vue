<template>
  <div id="app" class="container">
    <img alt="Vue logo" src="./assets/logoM.png" class="logo"/>
    <div id="nav">
      <router-link to="/">Home</router-link> |
      <router-link to="/settings">Settings</router-link>
    </div>
    <router-view />
  </div>
</template>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
#nav {
  padding: 30px;

  a {
    font-weight: bold;
    color: #2c3e50;

    &.router-link-exact-active {
      color: #42b983;
    }
  }
}
.container {
  max-width: 600px;
  margin: 0 auto;
}
.logo {
  width: 100px;
}
</style>
