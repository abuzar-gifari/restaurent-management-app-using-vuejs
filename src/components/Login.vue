<template>


  <img src="../assets/login_logo.jpg" style="width: 200px">
  <h1>Login</h1>

  <div class="login">
    <input type="email" v-model="email" name="" placeholder="enter email">
    <input type="password" v-model="password" name="" placeholder="enter password">
    <button v-on:click="login">Login</button>
    <p>
      <router-link to="sign-up">Sign Up</router-link>
    </p>
  </div>


</template>

<script>
import axios from "axios"
export default {
  name: 'Login',
  data(){
    return{
      email:"",
      password:""
    }
  },
  methods:{
    async login(){
      let result= await axios.get(
          `http://localhost:3000/users?email=${this.email}&password=${this.password}`
      );

      if (result.status==200 && result.data.length>0){
        // alert("sign up done");
        localStorage.setItem("user-info",JSON.stringify(result.data[0]));
        /*
            result.data is an object. we need to convert it in a string.
            that's why I use JSON.stringify();
         */
        this.$router.push({name:"Home"});
      }

      console.warn(result);
    }
  },
  mounted() {
    let user=localStorage.getItem("user-info");
    if (user){
      this.$router.push({ name:"Home" });
    }
  }

}
</script>

<style>

</style>
