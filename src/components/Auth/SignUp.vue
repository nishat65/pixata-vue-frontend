<template>
  <div>
    <div class="pixata-heading">Pixata</div>
    <form class="form-container" @submit.prevent="signUp()">
      <div class="heading">
        <div class="heading-signUp">SIGN UP</div>
      </div>
      <div>
        <div class="form-group">
          <label for="first-name">First Name</label>
          <input id="first-name" type="text" v-model="firstName" />
        </div>
        <div class="form-group">
          <label for="last-name">Last Name</label>
          <input id="last-name" type="text" v-model="lastName" />
        </div>
        <div class="form-group">
          <label for="username">Username</label>
          <input id="username" type="text" v-model="userName" />
        </div>
        <div class="form-group">
          <label for="email">Email</label>
          <input id="email" type="text" v-model="email" />
        </div>
        <div class="form-group">
          <label for="password">Password</label>
          <input id="password" type="text" v-model="password" />
        </div>
        <div class="form-group">
          <label for="confirm-password">Confirm Password</label>
          <input id="confirm-password" type="text" v-model="confirmPassword" />
        </div>
      </div>
      <div class="flex-center" style="margin: 1rem;">
        <button class="btn-submit" type="submit">Sign Up</button>
        <p>
          Already have an account?
          <router-link to="/signIn">SIGN IN</router-link>
        </p>
      </div>
    </form>
  </div>
</template>
<script lang="ts">
import { defineComponent } from "vue";

export default defineComponent({
  name: "SignUp",
  data() {
    return {
      firstName: "",
      lastName: "",
      userName: "",
      email: "",
      password: "",
      confirmPassword: ""
    };
  },
  methods: {
    signUp() {
      console.log(this.userName, this.password);
    }
  }
});
</script>

<style lang="scss">
.pixata-heading {
  text-align: center;
  margin: 2rem;
  font-size: 2rem;
}

.flex-center {
  display: flex;
  align-items: center;
  justify-content: center;
}

.heading {
  display: flex;
  width: 50%;
  align-items: center;
  margin: 12px auto;

  &-signUp {
    border: 1px solid white;
    text-align: center;
    color: #268c83;
    background: white;
    padding: 8px;
    font-weight: 800;
    font-size: 1.4rem;
  }
}

.form-container {
  width: 40%;
  margin: 1rem auto;
  display: flex;
  flex-direction: column;
  padding: 2rem;
  background: linear-gradient(to left bottom, #45a9a0, #fdfdfdbf),
    url(/img/pixatashare.d44ed658.jpg);
  background-size: cover;
  background-position: center;

  label {
    width: 7rem;
    font-size: 0.9rem;
  }

  input[type="text"] {
    border: 1px solid #66bfb7;
    outline: none;
    padding: 8px;
  }
}

.form-group {
  margin: 5px;
  display: flex;
  align-items: center;
  justify-content: center;
}

.btn-submit {
  width: 100px;
  padding: 10px;
  font-size: 1rem;
  margin: 12px;
  border: none;
  background: #268c83;
  color: white;
}
</style>
