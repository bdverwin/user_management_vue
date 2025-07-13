<script setup>
import { ref } from 'vue'


</script>


<template>
    <div class="form">
        <h1>USER FORM</h1>
        <form>
            <label>First name
                <input type="text" name="firstName">
            </label>
            <label>Last name
                <input type="text" name="lastName">
            </label>
            <label>Email
                <input type="email" name="Email">
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