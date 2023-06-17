<template>
  <div>
    <h1 class="head">User Details</h1>
    <div class="form" >
  <div class="card-body">
    <h5 class="card-title"><span>id: </span>{{ id }}</h5>
    <h5 class="card-title"><span>First Name: </span>{{ first_name }}</h5>
    <h5 class="card-title"><span>Last Name: </span>{{ last_name }}</h5>
    <h5 class="card-title"><span>Gender: </span>{{ gender }}</h5>
  </div>
</div>
  </div>
</template>

<script>
import axios from 'axios';
export default {
  name: "userdetailsApp",
  data(){
    return{
        id:'',
        first_name:'',
        last_name:'',
        gender:''
    }
  },
  created(){
    this.getuserById()
  },
  methods:{
    getuserById(){
      this.id = this.$route.params.id;
      console.log(this.id)
      axios.get(` http://localhost:3002/users/${this.id}`)
      .then((res)=>{
        console.log(res.data)
        this.id = res.data.id
        this.first_name = res.data.first_name
        this.last_name = res.data.last_name
        this.gender = res.data.gender
      })
      .catch((err)=>console.log(err))
    },
    back(){
        this.$router.push('/users')
    }
  }
};
</script>

<style scoped>
span{
  font-family: 'Satisfy', cursive;
  font-size: 24px;
  position:fixed;
  left: 35%; 
}
</style>
