<template>
  <div>
    <Header />
    <h1>Hello {{ firstName }}, Welcome to Penny-Save App</h1>
    <h2>Build up your savings steadily and earn interest with us.</h2>
    <h2>We offer:</h2>

    <!-- <h3>Education Savings, Personal Savings, Vacation Savings </h3> -->
    <div class="savingOptions">
      <button type="button" v-on:click="education">Education Savings</button>
      <button type="button" v-on:click="personal">Personal Savings</button>
      <button type="button" v-on:click="vacation">Vacation Savings</button>
    </div>

    <p>
      <router-link to="/sign-up"> Create New Account</router-link>
    </p>
    <p>
      <router-link to="/Login"> Login</router-link>
    </p>
  </div>
</template>

<script>
import Header from "./Header.vue";
// import axios from "axios";
export default {
  name: "Home",
  data() {
    return {
      firstName: "",
      saver: [],
    };
  },
  components: {
    Header,
  },
  async mounted() {
    let user = localStorage.getItem("user-info");
    // this.firstName = JSON.parse(user).firstName;
    if (!user) {
      this.$router.push({ name: "" });
      //removed this coz i want my customer to peruse the product
      //instead of forcing them to sign up 1st which can be a turn off
    }
    // let result = await axios.get("http://localhost:3000/savers");
    // console.warn(result);
    // this.saver = result.data;
  },
};
</script>

<!-- <style scoped>
table {
  width: 80%;
  border-radius: 2px;
}
tr,
td,
th,
table {
  border: 1px solid rgb(32, 86, 32);
}

th {
  background: #243d88;
  color: white;
  padding: 6px;
}

td {
  padding: 1px;
}
</style> -->

<style scoped>
h2 {
  color: black;

  margin-top: 20px;
  margin-bottom: 10px;
  text-align: center;
  font-size: 15px;
}
.savingOptions button {
  width: 320px;
  height: 40px;
  border: 2px solid green;
  background: rgb(175, 239, 175);
  color: black;
  cursor: pointer;
  border-radius: 4px;

  padding-left: 20px;
  display: block;
  margin-bottom: 30px;
  margin-right: auto;
  margin-left: auto;
}
</style>
