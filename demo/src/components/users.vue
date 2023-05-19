<template>
    <div>
    <table class="container">
        <h2>Users</h2>
        <tr>
            <th>Name</th>
            <th>Age</th>
            <th>Role</th>
        </tr>
        <tr v-for="user in filterUsers" :key="user.name">
            <td>{{ user.name }}</td>
            <td>{{ user.age }}</td>
            <td>{{ user.role }}</td>
            <button @click="deleteUser(user)" class="delete">Delete</button>
       </tr>
       </table>
    </div>
</template>

<script>
    export default {
        name:'UserPage',
        inject:['roles'],
        computed:{
            filterUsers(){
                return this.roles.filter((user) => user.role === 'user')
            }
        },
        methods: {
            deleteUser(user) {
            const index = this.roles.findIndex((a) => a.name === user.name);
            if (index !== -1) {
                this.roles.splice(index, 1);
            }
            }
        }
    }
</script>

<style scoped>

</style>