<template>
<div class="head">
    <img class='logo' src="../assets/logo.jpg" />
    <h1 class="login">Login</h1>
    <div class="login input">
        <input type="text" v-model="email" placeholder="Enter Your Email" />
        <input type="password" v-model="password" placeholder="Enter  Your Password" />
        <button v-on:click="login" class="login button">Login </button>
        <p>
            <router-link to='/sign-up'>Sign-Up</router-link>
        </p>
    </div>
</div>
</template>

<script>
import axios from 'axios'
export default {
    name: 'Login-component',
    data() {
        return {
            email: '',
            password: ''

        }
    },
    methods: {
        async login() {
            let result = await axios.get(
                `http://localhost:3000/users?email=${this.email}&password=${this.password}`
            )
            console.warn("Login", result);
            if (result.status == 200 && result.data.length > 0) {
                localStorage.setItem("user-info", JSON.stringify(result.data[0]));
                this.$router.push({
                    name: 'Home'
                })
            }
        }
    },
     mounted(){
       let user = localStorage.getItem('user-info');
       if(user){
            this.$router.push({name:'Home'})
       }
    }  
}

</script>

<style>

</style>
