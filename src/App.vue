<template>
<router-view/>
</template>

<script>


export default {
  name: 'App',

}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;

}
body{
  padding: 0;
  margin: 0;
}
.register input, .login input , .add input{
    width: 300px;
    height: 40px;
    padding-left: 20px;
    display: block;
    margin-bottom: 30px;
    margin-right: auto;
    margin-left: auto;
    border-block: 1px solid rgba(223, 153, 24, 0.774);
}

.register button, .login button, .add button {
    width: 100px;
    height: 40px;
    border: 1px solid rgba(223, 153, 24, 0.774);
    background: orange;
    color: blanchedalmond;
    cursor: pointer;
    
}
</style>
