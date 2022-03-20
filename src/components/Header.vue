<template>
<div class="nav">
    <a href="#">Home</a>
    <a href="#">Add Resturant</a>
    <a href="#">Update Resturant</a>
    <a v-on:click="logout" href="#">Logout</a>
</div>
</template>

<script>
export default {
    name: 'Header-component',
    methods:{
        logout() { 
                localStorage.clear();
                this.$router.push({name:'Login'})
            }
        }
    }
</script>

<style>
.nav {
    background-color: #333;
    overflow: hidden;
}

.nav a {
    float: left;
    color: #f2f2f2;
    text-align: center;
    padding: 10px 14px;
    text-decoration: none;
    font-size: 18px;
    margin-right: 5px;
}

.nav a:hover {
    background-color: #ddd;
    color: #222;
}
</style>
