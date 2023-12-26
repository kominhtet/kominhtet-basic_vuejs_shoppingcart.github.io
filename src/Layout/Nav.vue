<!-- App.vue -->
<template>
    <div>
        <nav class="navbar navbar-expand-lg navbar-light bg-body-tertiary">
        <div class="container-fluid">
            <a class="navbar-brand" href="#">VueJs</a>
            <button
            data-mdb-collapse-init
            class="navbar-toggler"
            type="button"
            data-mdb-target="#navbarNav"
            aria-controls="navbarNav"
            aria-expanded="false"
            aria-label="Toggle navigation"
            >
            <i class="fas fa-bars"></i>
            </button>
            <div class="collapse navbar-collapse" id="navbarNav">
            <ul class="navbar-nav">
                <li class="nav-item">
                <router-link class="nav-link active" aria-current="page" to="/">Home</router-link>
                </li>
                <li class="nav-item">
                <router-link class="nav-link" to="/product">Products</router-link>
                </li>
                <li class="nav-item">
                <router-link to="/cart" class="nav-link">
                    <i class="fas fa-cart-shopping"></i>
                    <small class="badge badge-danger" style="font-size: 9px;">{{ cart.length }}</small>
                </router-link>
                </li>   
            </ul>
            </div>
        </div>
        </nav>
    </div>
  </template>
  
  <script>
  
  export default {
    
    name: "NavPage",
    data(){
        return{
            cart:[]
        }
    },
    created(){
        this.cart = this.$root.cart;
    }
  };
  </script>