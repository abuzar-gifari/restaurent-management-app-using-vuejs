<template>
  <Header/>
  <h1>⭐Hello {{ name }} Welcome to Home Page⭐</h1>

  <table border="1" class="middle">
    <tr>
      <th>Id</th>
      <th>Name</th>
      <th>Contact</th>
      <th>Address</th>
      <th>Update</th>
      <th>Delete</th>
    </tr>
    <tr v-for="item in restaurant" :key="item.id">
      <td>{{ item.id }}</td>
      <td>{{ item.name }}</td>
      <td>{{ item.contact }}</td>
      <td>{{ item.address }}</td>
      <td><router-link :to="'/update/'+item.id">Update</router-link></td>
      <td><button @click="deleteRestaurent(item.id)">Delete</button></td>
    </tr>
  </table>

</template>

<script>
import Header from "./Header.vue"
import axios from "axios"
export default {
  name: 'Home',
  components:{
    Header
  },
  data(){
    return{
      name:"",
      restaurant:[]
    }
  },
  async mounted() {
    this.loadData();
  },
  methods:{
    async deleteRestaurent(id){
      let result = await axios.delete("http://localhost:3000/restaurent/"+id);
      if (result.status==200){
        this.loadData();
      }
    },
    async loadData(){
      let user=localStorage.getItem("user-info");
      this.name=JSON.parse(user).name;
      if (!user){
        this.$router.push({ name:"SignUp" });
      }

      let result = await axios.get("http://localhost:3000/restaurent");
      // console.warn(result);
      this.restaurant=result.data;
    }
  }
}
</script>

<style>
td{
  width:140px;
  height: auto;
}
.middle{
  margin-left: auto;
  margin-right: auto;
}
</style>
