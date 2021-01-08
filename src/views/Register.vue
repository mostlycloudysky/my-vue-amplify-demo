<template>
  <div class="container">
    <form @submit.prevent="register">
      <h2>Register</h2>
      <input type="email" v-model="email" placeholder="Email address.." />
      <input type="password" v-model="password" placeholder="Password.." />
      <button>Register</button>
    </form>
  </div>
</template>

<script>
import { Auth } from "aws-amplify";
export default {
  name: "Register",
  data() {
    return {
      email: "",
      password: ""
    };
  },
  methods: {
    async register() {
      try {
        await Auth.signUp({
          username: this.email,
          password: this.password,
          attributes: {
            email: this.email
          }
        });
        alert("User successfully registered. Please login");
      } catch (err) {
        alert(err.message);
      }
    }
  }
};
</script>

<style></style>
