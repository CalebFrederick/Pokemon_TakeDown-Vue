<template>
  <nav class="navbar navbar-light bg-light">
    <a class="navbar-brand" href="#">
      <img src="./assets/Pokeball.png" width="50" height="50" alt="" />
    </a>
    <router-link to="/">Home</router-link> |
    <router-link to="/about">About</router-link> |
    <router-link to="/takedown">Takedown</router-link> |
    <router-link to="/signup">Signup</router-link> |
    <router-link to="/login">Login</router-link> |
    <router-link to="/pokemon">Party Pokemon</router-link> |
    <!-- <router-link to="/party">Party Pokemon</router-link> | -->
    <router-link to="/logout">Logout</router-link>
  </nav>
  <router-view />
</template>

<style>
#app {
  font-family: Pokemon, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #fbfbfb;

  background-color: #2c3e50;
}

@font-face {
  font-family: Pokemon;
  src: url(./assets/Pokemon-Normal.ttf);
}

nav {
  padding: 50px;
}

nav a {
  font-weight: bold;
  color: #f9fbfb;
}

nav a.router-link-exact-active {
  color: #fc3034;
}
</style>
