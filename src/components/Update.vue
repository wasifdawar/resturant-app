<template>
<div>
<Header/>
<h1>Welcome to Update Restaurant page</h1>   
</div> 
</template>

<script>
import Header from './Header.vue'
export default {
    name: "Update-Restaurant",
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
