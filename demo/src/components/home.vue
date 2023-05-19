<template>
    <div>
        <button @click="selectedComponent = 'FormPage'">Form</button>
        <button @click="selectedComponent = 'UserPage'">Users</button>
        <button @click="selectedComponent = 'AdminPage'">Admin</button>

        <component :is="selectedComponent" v-if="selectedComponent" @formSubmitted="handleFormSubmission" />
    </div>
</template>

<script>
import FormPage from './form.vue'
import UserPage from './users.vue'
import AdminPage from './admins.vue'
    export default {
        name: 'HomePage',
        components: {
            FormPage,
            UserPage,
            AdminPage
        },
        data() {
            return {
            selectedComponent: FormPage,
            roles:[
                {"name":"Samar", "age":"23", "role":"admin"},
                {"name":"Samir", "age":"23", "role":"admin"},
                {"name":"Samy", "age":"60", "role":"admin"},
                {"name":"Fatma", "age":"23", "role":"user"},
                {"name":"Islam", "age":"26", "role":"user"},
                {"name":"Ahmed", "age":"40", "role":"user"}
            ]
            };
        },
          methods: {
                handleFormSubmission(formValues) {
                this.roles.push(formValues);
                console.log(this.roles);
            }
        },
        provide(){
            return {roles: this.roles};
        }
    }
</script>
<style scoped>
button{
 background-color: #9384D1;
 font-size: 20px;
 font-family:monospace
}
</style>