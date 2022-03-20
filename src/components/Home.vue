<template>
<div>
<Header/>
<h1>Welcome to Home page</h1>   
</div> 
</template>

<script>
import Header from './Header.vue'
export default {
    name: "Home-componnet",
    components:{
        Header
        } ,
     mounted(){
       let user = localStorage.getItem('user-info');
       if(!user){
            this.$router.push({name:'SignUp'})
       }
    }
}
</script>

<style>

</style>
