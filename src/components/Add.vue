<template>
  <Header/>
  <h1>Hello user welcome to Add Restaurent page</h1>

  <form action="" method="post" class="add">
    <input type="text" name="name" placeholder="Enter Name" v-model="restaurent.name">
    <input type="text" name="contact" placeholder="Enter Contact" v-model="restaurent.contact">
    <input type="text" name="address" placeholder="Enter Address" v-model="restaurent.address">
    <button type="button" v-on:click="addRestaurent">Add New Restaurent</button>
  </form>


</template>

<script>

import Header from "./Header.vue"
import axios from "axios"

export default {
  name: 'Add',
  components:{
    Header
  },
  data(){
    return{
      restaurent:{
        name:"",
        contact:"",
        address:""
      }
    }
  },
  methods:{
    async addRestaurent(){
      console.warn(this.restaurent);
      const result = await axios.post("http://localhost:3000/restaurent",{
          name:this.restaurent.name,
          contact:this.restaurent.contact,
          address:this.restaurent.address
      });
      if (result){
        this.$router.push({ name:"Home" });
      }
      console.warn("result",result);
    }
  },
  mounted() {
    let user=localStorage.getItem("user-info");
    if (!user){
      this.$router.push({ name:"SignUp" });
    }
  }
}
</script>

<style>

</style>
