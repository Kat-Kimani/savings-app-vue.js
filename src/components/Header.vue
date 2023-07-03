<template>
  <div class="nav">
    <router-link to="/" href="#"> Home</router-link>
    <router-link to="/add" href="#"> Add Transaction</router-link>
    <router-link to="/update" href="#"> Update Saver</router-link>
    <router-link to="/savers" href="#"> Savers Master</router-link>
    <a v-on:click="logout" href="#"> Logout</a>
  </div>
</template>

<script>
export default {
  name: "Header",
  methods: {
    logout() {
      // console.warn("logout")
      localStorage.clear();
      this.$router.push({ name: "Login" });
    },
  },
};
</script>

<style>
.nav {
  background-color: rgb(198, 244, 222);
  overflow: hidden;
}

.nav a {
  float: left;
  font-size: 17px;
  font-weight: bold;
  padding: 14px 16px;
  text-align: center;
  text-decoration: none;
  margin-right: 5px;
}
.nav a:hover {
  background: whitesmoke;
  color: black;
}
</style>
