<template>
<navbarApp v-if="!$route.meta.hideNavbar"/>
<router-view></router-view>
</template>

<script>
import navbarApp from "./components/pages/navbar.vue"
export default {
  name: 'App',
  components: {
    navbarApp
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  /* margin-top: 60px; */
}
.form{
  width: 40%;
  margin: 3% auto;
  border: 1px solid black;
  padding: 2%;
  border-radius: 10px;
}
.head{
  margin-top:3%;
  font-family: 'Philosopher', sans-serif;
}
</style>
