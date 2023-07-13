<!-- PageHome.vue -->
<template>
    <div class="home">
      <img alt="Vue logo" src="../assets/logo.png">
      <HelloWorld msg="Welcome to Your Vue.js App"/>
    </div>
  </template>
  
  <script>
  // @ is an alias to /src
  import HeaderComponent from "./components/HeaderComponent.vue"
  
  export default {
    name: 'PageHome',
    components: {
        HeaderComponent
    }
  }
  </script>