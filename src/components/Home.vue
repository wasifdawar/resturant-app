<template>
<h1>Welcome to Home page</h1>    
</template>

<script>
export default {
    name: "Home-componnet",
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
