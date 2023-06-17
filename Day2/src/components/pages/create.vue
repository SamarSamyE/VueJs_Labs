<template>
  <div>
    <h1 class="head">Add New User</h1>
    <form @submit.prevent="addUser" class="form">
      <div class="d-flex flex-column">
        <label for="first_name">First Name</label>
        <input type="text" v-model="first_name" id="first_name" required>
      </div>
      <div class="d-flex flex-column">
        <label for="last_name">Last Name</label>
        <input type="text" v-model="last_name" id="last_name" required>
      </div>
      <div class="d-flex flex-column">
        <label for="gender">Gender</label>
        <input type="text" v-model="gender" id="gender" required>
      </div>
      <div class="mt-3">
        <button type="submit">Add User</button>
      </div>
    </form>
  </div>
</template>

<script>
import axios from 'axios';

export default {
  name:'adduserApp',
  data() {
    return {
      first_name: '',
      last_name: '',
      gender: ''
    };
  },
  methods: {
    addUser() {
      axios.post('http://localhost:3002/users', {
        first_name: this.first_name,
        last_name: this.last_name,
        gender: this.gender
      })
        .then((res) => {
          console.log(res.data);
          this.$router.push('/users');

        })
        .catch((err) => console.log(err));
    }
  }
};
</script>
<style scoped>
input{
  width: 60%;
  margin: auto
}
label{
  font-family: 'Satisfy', cursive;
  font-size: 24px
}
button{
  font-family: 'Cormorant Garamond', serif;
  font-size: 24px;
  border: none;
  background: #454545;
  color: white
}
</style>