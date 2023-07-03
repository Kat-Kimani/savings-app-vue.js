<template>
  <div>
    <h1>Sign Up</h1>
    <div class="register">
      <input
        type="text"
        v-model="firstName"
        placeholder="First Name"
        required
      />
      <input type="text" v-model="lastName" placeholder="Last Name" required />

      <input
        type="tel"
        v-model="phone"
        placeholder="Phone Contact"
        required
        minlength="2"
      />
      <input
        type="text"
        v-model="idNumber"
        placeholder="ID Number/Passport"
        required
        minlength="2"
      />
      <input
        type="email"
        v-model="email"
        placeholder="Email@example.com"
        required
      />
      <input
        type="password"
        v-model="password"
        placeholder="Enter Password"
        required
        minlength="2"
      />
      <button v-on:click="signUp">Create New Account</button>
      <p>
        <router-link to="/Login"> Login</router-link>
      </p>
    </div>
  </div>
</template>

<script>
import axios from "axios";
export default {
  name: "SignUp",
  data() {
    return {
      firstName: "",
      lastName: "",
      phone: "",
      idNumber: "",
      email: "",
      password: "",
    };
  },
  methods: {
    async signUp() {
      // Validate the form inputs
      if (!this.validateForm()) {
        return;
      }

      // console.warn("signup", this.name, this.email, this.password )
      let result = await axios.post("http://localhost:3000/savers", {
        firstName: this.firstName,
        lastName: this.lastName,
        phone: this.phone,
        idNumber: this.idNumber,
        email: this.email,
        password: this.password,
      });
      console.warn(result);
      if (result.status == 201) {
        // alert("sign-up successful");
        localStorage.setItem("user-info", JSON.stringify(result.data));
        this.$router.push({ name: "Home" });
      }
    },
    validateForm() {
      // Perform form validation here
      if (
        !this.firstName ||
        !this.lastName ||
        !this.phone ||
        !this.idNumber ||
        !this.email ||
        !this.password
      ) {
        alert("Please fill in all fields.");
        return false;
      }

      return true;
    },
  },

  mounted() {
    let user = localStorage.getItem("user-info");
    if (user) {
      this.$router.push({ name: "Home" });
    }
  },
};
</script>
