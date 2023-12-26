<!-- App.vue -->
<template>
    <div>
        <!-- Nav -->
        <Nav />
        <!-- Content -->
        <slot />
    </div>
  </template>
  
  <script>
  import Nav from './Nav';
  export default {
    components:{Nav},
    name: "MasterPage",
  };
  </script>