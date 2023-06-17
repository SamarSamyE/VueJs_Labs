<template>
  <div class="container container-fluid-sm">
    <div class="d-flex">
          <h4 class="mb-4">All Users</h4>
          <router-link :to="'/create'" class="btn btn-sm btn-success ms-2 add">Add User <span>+</span></router-link>
    </div>

    <table class="table table-striped">
      <thead>
        <tr>
          <th scope="col">Id</th>
          <th scope="col">First Name</th>
          <th scope="col">Last Name</th>
          <th scope="col">Actions</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="user in users" :key="user.id">
          <th scope="row">{{ user.id }}</th>
          <td>{{ user.first_name }}</td>
          <td>{{ user.last_name }}</td>
          <td>
            <router-link :to="`/users/${user.id}`" class="btn btn-sm btn-secondary ms-2">Show</router-link>
            <router-link :to="`/update/${user.id}`" class="btn btn-sm btn-info ms-2 me-2">Update</router-link>
            <button class="btn btn-sm btn-danger" @click="deleteUser(user.id)">Delete</button>
          </td>
        </tr>
      </tbody>
    </table>
  </div>
</template>


<script>
import axios from "axios";
export default {
  name: "allusersApp",
  created() {
    this.getallusers();
  },
  data() {
    return {
      users: [],
    };
  },
  methods: {
    getallusers() {
      axios
        .get(" http://localhost:3002/users")
        .then((res) => {
          console.log(res.data);
          this.users = res.data
        })
        .catch((err) => console.log(err));
    },
    deleteUser(id){
        axios.delete(`  http://localhost:3002/users/${id}`)
        .then((res)=>{
            console.log(res.data)
            this.getallusers()
        })
        .catch((err)=>console.log(err))
    }
  },
};
</script>

<style scoped>
.add{
  position: relative;
  left: 80%;
 margin-top: 2%;
 padding: 10px
}
</style>
