<template>
    <div>
      
       <table class="container">
        <h2>Admins</h2>
        <tr>
            <th>Name</th>
            <th>Age</th>
            <th>Role</th>
        </tr>
        <tr v-for="admin in filterAdmins" :key="admin.name">
            <td>{{ admin.name }}</td>
            <td>{{ admin.age }}</td>
            <td>{{ admin.role }}</td>
            <button @click="deleteAdmin(admin)" class="delete">Delete</button>
       </tr>
       </table>
    </div>
</template>

<script>
    export default {
        name:'AdminPage',
        inject:['roles'],
        computed:{
            filterAdmins(){
                return this.roles.filter((admin) => admin.role === 'admin')
            }
        },
        methods: {
            deleteAdmin(admin) {
            const index = this.roles.findIndex((a) => a.name === admin.name);
            if (index !== -1) {
                this.roles.splice(index, 1);
            }
            }
        }
    }
</script>

<style scoped>

</style>