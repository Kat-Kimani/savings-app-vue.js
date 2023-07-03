<template>
  <router-view />
</template>

<script setup>
// import SignUp from './components/SignUp.vue'
</script>

<style>
h1{
  color: rgb(32 195 32);
  font-size: 20;
  font-weight: bold;
  margin-top: 20px;
  margin-bottom: 10px;
  text-align: center;
}


body {
  padding: 0;
  margin: 0;
}

.register,
.login .addtrans {
  display: flex;
  flex-direction: column;
  align-items: center;
}
.register input,
.login input,
.addtrans input {
  width: 300px;
  height: 40px;
  padding-left: 20px;
  display: block;
  margin-bottom: 30px;
  margin-right: auto;
  margin-left: auto;

  border: 2px solid rgb(27, 162, 27);
  border-radius: 4px;
}

.register button,
.login button,
.addtrans button {
  width: 320px;
  height: 40px;
  border: 2px solid green;
  background: rgb(175, 239, 175);
  color: black;
  cursor: pointer;
  border-radius: 4px;
}


</style>

<style scoped>
header {
  line-height: 1.5;
}
/* 
.logo {
  display: block;
  margin: 0 auto 2rem;
} */

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  .logo {
    margin: 0 2rem 0 0;
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }
}
</style>
