<template>
  <nav>
    <router-link to="/">Home</router-link> |
    <router-link :to="{ name: 'About' }">About</router-link> |
    <router-link :to="{ name: 'Jobs' }">Jobs</router-link>
  </nav>
  <button class="nav-button" @click="redirect">Redirect</button>
  <button class="nav-button" @click="goBack">Go Back</button>
  <button class="nav-button" @click="goForward">Go Forward</button>
  <router-view />
</template>

<script>
export default {
  methods: {
    redirect() {
      this.$router.push({ name: 'Jobs' });
    },
    goBack() {
      this.$router.go(-1);
    },
    goForward() {
      this.$router.go(1);
    },
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
}

nav {
  padding: 30px;
}

nav a:hover {
  background-color: #ffb3b3;
}

nav a {
  font-weight: bold;
  color: #2c3e50;
  text-decoration: none;
  padding: 10px;
  border-radius: 10px;
}

nav a.router-link-exact-active {
  color: #ffffff;
  background-color: #ff2222;
}
.nav-button {
  margin: 10px;
  padding: 10px;
  background: rgb(28, 116, 50);
  border-radius: 10px;
  color: white;
  cursor: pointer;
  border: none;
}
.nav-button:hover {
  background: rgb(36, 176, 139);
}
</style>
