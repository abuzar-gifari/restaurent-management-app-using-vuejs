<template>
  <router-view/>
</template>

<script>

export default {
  name: 'App'
}
</script>

<style>
body{
  margin: 0;
  padding: 0;
}
#app {
  font-family: "Source Sans Pro";
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  /*margin-top: 60px;*/
}
.register input, .login input, .add input{
  width: 300px;
  height: 40px;
  padding-left: 20px;
  display: block;
  margin-bottom: 30px;
  margin-left: auto;
  margin-right: auto;
  border: 1px solid blue;
}
.register button, .login button, .add button{
  width: 320px;
  height: 40px;
  border: 1px solid blue;
  background: skyblue;
  color: white;
  cursor: pointer;
}
</style>
