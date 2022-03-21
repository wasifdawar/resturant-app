<template>
<div>
    <Header />
    <h1>Welcome {{name}} to Home page</h1>
    <table border="1px">
            <tr>
            <td>ID</td>
            <td>Name</td>
            <td>Address</td>
            <td>Contact</td>
            <td>Actions</td>
        </tr>
        <tr v-for="item in restaurants" :key="item.id">
            <td>{{item.id}}</td>
            <td>{{item.name}}</td>
            <td>{{item.address}}</td>
            <td>{{item.contact}}</td>
            <td><router-link :to="'/update'+item.id">Update</router-link></td>
        </tr>

    </table>
</div>
</template>

<script>
import axios from 'axios'
import Header from './Header.vue'
export default {
    name: "Home-componnet",
    data() {
        return {
            name: '',
            restaurants: [],
        }
    },
    components: {
        Header
    },
    async mounted() {
        let user = localStorage.getItem('user-info');
        this.name = JSON.parse(user).name
        if (!user) {
            this.$router.push({
                name: 'SignUp'
            })
        }
        let result = await axios.get("http://localhost:3000/restaurant");
        console.warn(result);
        this.restaurants = result.data;
    }
}
</script>

<style>
td{
 width: 160px;
 height: 40px
}
</style>
