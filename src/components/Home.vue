<template>
    <Header></Header>
    <h1>hello {{ name }}, Welcome to the home page!!</h1>
    <table border="1px">
        <tr>
            <td>ID</td>
            <td>NAME</td>
            <td>CONTACT</td>
            <td>ADDRESS</td>
            <td>ACTIONS</td>
        </tr>
        <tr v-for="item in restaurent" :key="item.id">
            <td>{{ item.id }}</td>
            <td>{{ item.name }}</td>
            <td>{{ item.contact }}</td>
            <td>{{ item.address }}</td>
            <td>
                <router-link :to="'/update/' + item.id">Update</router-link> &nbsp;
                <button v-on:click="deleteRestaurant(item.id)">Delete</button>
            </td>
        </tr>
    </table>
</template>
<script>
import Header from "./Header.vue";
import axios from "axios";
export default {
    name: "Home",
    data() {
        return {
            name: "",
            restaurent: [],
        };
    },
    components: {
        Header,
    },
    methods: {
       async deleteRestaurant(id) 
        {
            //console.warn(id)
            let result =await axios.delete("http://localhost:3000/restaurant/"+id);
            console.warn(result)
            if(result.status == 200){
                this.loadData()
            }
        },
        async loadData() {
            let user = localStorage.getItem("user-info");
            this.name = JSON.parse(user).name;
            if (!user) {
                this.$router.push({ name: "SignUp" });
            }
            let result = await axios.get("http://localhost:3000/restaurant");

            console.warn(result);
            this.restaurent = result.data;
        }
    },
    async mounted() {
        this.loadData();
    },
};
</script>
<style>
td {
    width: 150px;
    height: 50px;
}
</style>
