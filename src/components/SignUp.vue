<template>
<div class="head">
<img class='logo' src="../assets/logo.jpg" />
<h1 class="signup">SignUp</h1>
<div class="register input">
    <input type="text" v-model="name" placeholder="Enter Your Name" />
    <input type="text" v-model="email" placeholder="Enter Your Email" />
    <input type="password" v-model="password" placeholder="Enter  Your Password" />
    <button v-on:click="signUP" class="register-buitton">Sign Up </button>
</div>
</div>
</template>

<script>
import axios from 'axios';

export default {
    name: 'SignUp',
    data(){
        return {
            name:'',
            email:'',
            password:''
        }
    },
    methods:{
        async signUP(){
            console.warn("signUP", this.name, " +++" , this.email);
            let result = await axios.post("http://localhost:3000/users",{
                email:this.email,
                name: this.name,
                password: this.password
            });
            console.warn(result);
            if(result.status==201)
            {
            localStorage.setItem("user-info",JSON.stringify(result.data));
            this.$router.push({name:'Home'})
        }}

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
.logo {
    width: 100px
}
.register input
{
    text-align: center;
    width: 300px;
    height: 40px;
    display: block;
    margin-bottom: 30px;
    margin-left: auto;
    margin-right: auto;
    border: 1px solid skyblue;
}

.register button{
    text-align: center;
    width: 308px;
    height: 40px;
    display: block;
    margin-bottom: 30px;
    margin-left: auto;
    margin-right: auto;
    border: 1px solid skyblue;
    background-color: skyblue;
    color: white;
}
</style>
