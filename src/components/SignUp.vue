<template>
  <img src="../assets/login_logo.jpg" style="width: 200px">
<h1>Sign Up</h1>

  <div class="register">
    <input type="text" v-model="name" name="" placeholder="enter name">
    <input type="email" v-model="email" name="" placeholder="enter email">
    <input type="password" v-model="password" name="" placeholder="enter password">
    <button v-on:click="signUp()">Sign Up</button>
    <p>
      <router-link to="login">Login</router-link>
    </p>
  </div>

</template>

<script>
import axios from "axios"
// npm install axios
export default {
  name:"SignUp",
  data(){
    return{
      name:"",
      email:"",
      password:""
    }
  },
  methods:{
    async signUp(){
      let result = await axios.post("http://localhost:3000/users",{
        name:this.name,
        email:this.email,
        password:this.password
      });

      console.warn(result);
      if (result.status==201){
        // alert("sign up done");
        localStorage.setItem("user-info",JSON.stringify(result.data));
        /*
            result.data is an object. we need to convert it in a string.
            that's why I use JSON.stringify();
         */
        this.$router.push({name:"Home"});
      }

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
