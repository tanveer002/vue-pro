<template>
    <h1>Signup</h1>
    <Signup />
    
</template>

<script>
  import Signup from './components/Signup.vue';

  export default{
    name: 'App',
    components: { Signup }
    
    }
   
  
</script>

<style>
  #app{
    text-align:center;
    color:#444;
    margin-top:60px;
  }
  body{
    margin: 0px;
    background: #eee;
  }
</style>



