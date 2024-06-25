<template>
    <Header></Header>
  <h1>hello User, Welcome to the Add Restaurant page!!</h1>
  <form action="" class="add">
    <input type="text" name="name" placeholder="Enter Name" v-model="restaurant.name">
    <input type="text" name="address" placeholder="Enter Address" v-model="restaurant.address">
    <input type="text" name="contact" placeholder="Enter Contact" v-model="restaurant.contact">
    <button type="button" v-on:click="addRestaurant"> Save</button>
  </form>
</template>
<script>
import axios from "axios";
import Header from "./Header.vue";
export default {
  name: "Add",
  components: {
    Header,
  },
  data(){
    return {
      restaurant:{
        name:'',
        address:'',
        contact:''
      }
    }
  },

  methods:{
  async  addRestaurant(){
      console.warn(this.restaurant);
      const result = await axios.post("http://localhost:3000/restaurant", {
        name: this.restaurant.name,
        address: this.restaurant.address,
        contact: this.restaurant.contact
      });

      if(result.status == 201){
        this.$router.push({name: 'Home'})
      }
      console.warn("result", result);
    }
  },
  mounted() {
    let user = localStorage.getItem("user-info");
    if (!user) {
      this.$router.push({ name: "SignUp" });
    }
  },
};
</script>
