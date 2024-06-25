<template>
    <div class="nav">

        <router-link  to="/">Home</router-link>
        <router-link  to="/add">Add Restaurant</router-link>
        <!-- <router-link to="/update">Update Restaurant</router-link> -->
        <a v-on:click="logout" href="#">Logout</a>
    </div>
</template>

<script>
export default {
    name: 'Header',
    methods:{
        logout(){
            localStorage.clear();
            this.$router.push({name: 'Login'})
        }
    }
}
</script>
<style>
.nav{
    background-color: rgb(59, 55, 47);
    overflow: hidden;
}
.nav a {
    float: left;
    color: rgb(247, 186, 73);
    padding: 15px 15px;
    text-align: center;
    font-size: 20px;
    text-decoration: none;
    font-family: math;
    margin-right: 5px;
}
.nav a:hover{
    background: rgb(247, 186, 73);
    color: black
    
}
</style>