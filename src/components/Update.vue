<template>
  <Header/>
  <h1>Hello user welcome to Update Restaurent page page</h1>

  <form action="" method="post" class="add">
    <input type="text" name="name" placeholder="Enter Your Name" v-model="restaurent.name">
    <input type="text" name="contact" placeholder="Enter Your Contact" v-model="restaurent.contact">
    <input type="text" name="address" placeholder="Enter Your Address" v-model="restaurent.address">
    <button type="button" v-on:click="updateRestaurent">Update Restaurent</button>
  </form>


</template>

<script>
import Header from "./Header.vue"
import axios from "axios"
export default {
  name: 'Update',
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
  async mounted() {
    let user=localStorage.getItem("user-info");
    if (!user){
      this.$router.push({ name:"SignUp" });
    }
    // console.warn(this.$route.params.id);
    const result = await axios.get("http://localhost:3000/restaurent/"+this.$route.params.id);
    this.restaurent=result.data;
  },
   methods:{
     async updateRestaurent(){
      const result = await axios.put("http://localhost:3000/restaurent/"+this.$route.params.id,{
        name:this.restaurent.name,
        contact:this.restaurent.contact,
        address:this.restaurent.address
      });
      if (result.status==200){
        this.$router.push({ name:"Home" });
      }
    }
  }
}
</script>

<style>

</style>
