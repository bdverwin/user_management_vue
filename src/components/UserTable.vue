<script setup>
import Axios from "axios"
import { ref, onMounted } from 'vue'

const users = ref([]);
const link = "http://localhost:8080/user"

const getUsers = async () => {
    try {
        const response = await Axios(link + "/all");
        users.value = response.data;
        console.log(users.value);
    } catch (err) {
        console.log(err);
    }
}

const dateFormatter = (date) => {
    const formatted = new Date(date).toLocaleDateString('en-US', {
        year: 'numeric',
        month: 'long', 
        day: 'numeric'
    })

    return formatted;
}

onMounted(() => {
    getUsers();
})

</script>


<template>
    <div class="content">
        <h1>List of Users</h1>
        <table>
            <thead>
                <tr>
                    <th>ID</th>
                    <th>First Name</th>
                    <th>Last Name</th>
                    <th>Email</th>
                    <th>Created At</th>
                    <th>Updated At</th>
                </tr>
            </thead>
            <tbody>
                <tr v-for="user in users" :key="user.id">
                    <td>{{ user.id }}</td>
                    <td>{{ user.firstName }}</td>
                    <td>{{ user.lastName }}</td>
                    <td>{{ user.email }}</td>
                    <td>{{ dateFormatter(user.createdAt) }}</td>
                    <td>{{ dateFormatter(user.updatedAt) }}</td>
                </tr>
            </tbody>
        </table>
    </div>

</template>

<style>
td, th{
    padding:10px;
    text-align: center;
    border:1px solid rgba(240, 248, 255, 0.459);
    min-width:130px;
}
table{
    border-collapse: collapse;
}
div.content{
    display:flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
}

th{
    background-color: rgba(187, 223, 255, 0.459);
    color:black;
}

</style>