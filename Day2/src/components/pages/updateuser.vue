<template>
  <div>
    <h1 class="head">Edit User</h1>
    <form @submit.prevent="updateUser" class="form">
      <div class="d-flex flex-column">
        <label for="first_name">First Name:</label>
        <input type="text" v-model="first_name" id="first_name" required>
      </div>
      <div class="d-flex flex-column">
        <label for="last_name">Last Name:</label>
        <input type="text" v-model="last_name" id="last_name" required>
      </div>
      <div class="d-flex flex-column">
        <label for="gender">Gender:</label>
        <input type="text" v-model="gender" id="gender" required>
      </div>
      <div class="mt-3">
        <button type="submit">Update User</button>
      </div>
    </form>
  </div>
</template>

<script>
import axios from 'axios';

export default {
    name: "updateuserApp",
  data() {
    return {
      id: null,
      first_name: '',
      last_name: '',
      gender: ''
    };
  },
  mounted() {
    this.getUserById();
  },
  methods: {
    getUserById() {
      this.id = this.$route.params.id;
      axios.get(`http://localhost:3002/users/${this.id}`)
        .then((res) => {
          this.first_name = res.data.first_name;
          this.last_name = res.data.last_name;
          this.gender = res.data.gender;
        })
        .catch((err) => console.log(err));
    },
    updateUser() {
      axios.put(`http://localhost:3002/users/${this.id}`, {
        id: this.id,
        first_name: this.first_name,
        last_name: this.last_name,
        gender: this.gender
      })
        .then((res) => {
            this.$router.push('/users');
            console.log(res.data);
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
