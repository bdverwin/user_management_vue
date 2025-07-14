<script setup>
import { ref, onMounted } from 'vue'
import axios from 'axios';
import { useRoute, useRouter } from 'vue-router';

const link = "http://localhost:8080/user";
const user = ref([]);
const updateValue = ref({
    firstName : '',
    lastName : '',
    email : '',
})
const route = useRoute();
const router = useRouter();
const id = route.params.id;

const updateUser = async () => {
    try {
        const response = await axios.put(link + '/update/' + id, updateValue.value)
        window.alert(response.data.message);
        router.push('/');
    } catch (error) {
        console.log(error);
    }
}


onMounted(async () => {
    try {
        const response = await axios.get(link + '/' + id)
        const {firstName, lastName, email} = response.data;
        updateValue.value.firstName = firstName;
        updateValue.value.lastName = lastName;
        updateValue.value.email = email;
        console.log(updateValue.value);
    } catch (error) {
        console.log(error);
    }
})

</script>


<template>
    <div class="form">
        <h1>USER FORM</h1>
        <form @submit.prevent="updateUser">
            <label>First name
                <input v-model="updateValue.firstName">
            </label>
            <label>Last name
                <input v-model="updateValue.lastName">
            </label>
            <label>Email
                <input v-model="updateValue.email">
            </label>
            <button type="submit" class="submit">SUBMIT</button>
        </form>
    </div>
</template>


<style>

div.form{
    padding:40px;
    border:1px solid rgb(255, 255, 255);
    max-width:500px;
    display:flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    border-radius: 10px;
    min-height: 500px;
}
div.form form{
    width:100%;
}

div.form label, input, button{
    display:block;
    width:100%;
}

div.form input{
    padding:10px 15px;
    border-radius: 5px;
}

div.form label{
    margin-bottom:20px;
}

div.form button.submit{
    margin:auto;
    padding:10px;
    max-width: 200px;
    margin-top:30px;
}

</style>