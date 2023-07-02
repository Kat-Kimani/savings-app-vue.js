<template>
  <div>
    <Header />
    <h1>Hello {{ firstName }}, Welcome to Penny-Save App</h1>
    <table>
      <thead>
        <tr>
          <th>Customer ID</th>
          <th>First Name</th>
          <th>Last Name</th>
          <th>Phone</th>
          <th>National ID</th>
          <th>Email</th>
        </tr>
      </thead>
      <tr v-for="item in saver" :key="item.id">
        <td>{{ item.id }}</td>
        <td>{{ item.firstName }}</td>
        <td>{{ item.lastName }}</td>
        <td>{{ item.phone }}</td>
        <td>{{ item.idNumber }}</td>
        <td>{{ item.email }}</td>
      </tr>
    </table>
  </div>
</template>

<script>
import Header from "./Header.vue";
import axios from "axios";
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
    let result = await axios.get("http://localhost:3000/savers");
    console.warn(result);
    this.saver = result.data;
  },
};
</script>

<style scoped>
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
</style>
