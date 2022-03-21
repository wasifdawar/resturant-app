<template>
<div>
<Header/>
<h1>Welcome to Add Restaurant page</h1>   
<form class="add">
    <input type='text' placeholder="Enter Name" v-model="restaurant.name" name="name"/>
    <input type='text' placeholder="Enter Address" v-model="restaurant.address" name="address"/>
    <input type='number' placeholder="Enter Contact" v-model="restaurant.contact" name="contact"/>
    <button type="button" v-on:click="addrestaurant()">Add Restaurant</button>
</form>
</div> 
</template>

<script>
import Header from './Header.vue';
import axios from 'axios';
export default {
    name: "Add-Restaurant",
    data(){
        return{
            restaurant:{
            name:'',
            address:'',
            contact:''
        }}
    },
    components:{
        Header
        } ,
        methods:{
            async addrestaurant(){
                const result = await axios.post("http://localhost:3000/restaurant",{
                    name: this.restaurant.name,
                    address: this.restaurant.address,
                    contact: this.restaurant.contact,
                });
                if(result.status==201){
                    this.$router.push({name:'Home'});
                }
                console.warn("result",result);
            }
        },
     mounted(){
       let user = localStorage.getItem('user-info');
       if(!user){
            this.$router.push({name:'SignUp'})
       }
    }
}
</script>

<style>

.add{

}
</style>
