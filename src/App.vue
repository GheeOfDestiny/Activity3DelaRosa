<template>
  <nav>
    <router-link :to="homeLink">Home Page</router-link> |
    <router-link :to="shopLink" @click="navigateToShop">Shop</router-link>
  </nav>
  <router-view/>
</template>

<script>
export default {
  data()
  {
    return {
      isLoggedIn: false
    };
  },
  computed: {
    shopLink()
    {
      return this.isLoggedIn ? '/shop' : '#'; 
    },
    homeLink()
    {
      return this.$route.path === '/shop' ? '#' : '/'; 
    }
  },
  methods: {
    navigateToShop(event)
    {
      if (!this.isLoggedIn)
      {
        event.preventDefault(); 
        console.log("You need to be logged in to access the Shop.");
      }
    }
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
}

nav {
  padding: 30px;
}

nav a {
  font-weight: bold;
  color: #2c3e50;
}

nav a.router-link-exact-active {
  color: #42b983;
}
</style>
