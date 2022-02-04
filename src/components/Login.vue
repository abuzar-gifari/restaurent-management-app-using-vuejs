<template>


  <img src="../assets/login_logo.jpg" style="width: 200px">
  <h1>Login</h1>

  <div class="login">
    <input type="email" v-model="email" name="" placeholder="enter email">
    <input type="password" v-model="password" name="" placeholder="enter password">
    <button>Login</button>
    <p>
      <router-link to="sign-up">Sign Up</router-link>
    </p>
  </div>


</template>

<script>

export default {
  name: 'Login',

}
</script>

<style>

</style>
