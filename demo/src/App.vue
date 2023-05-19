<template>
    <HomePage/>
</template>

<script>
import HomePage from './components/home.vue'
export default {
  name: "App",
  components:{
  HomePage
  },
  
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
button{
  cursor: pointer;
  padding: 1% 2%;
  border: none;
  border-radius: 10px;
  margin: 0% 2% 
}
.container{
  width: 40%;
    margin: 2% auto;
    border: 1px solid black;
    padding: 2%;
    border-radius: 10px;
}
.delete{
  background-color: red;
  padding: 5% 10%
}
</style>
