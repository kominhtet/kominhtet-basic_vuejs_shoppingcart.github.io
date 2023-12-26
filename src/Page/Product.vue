<template>
    <Master>
      <Loader v-show="isLoad" />
      <div v-show="!isLoad" class="container">
        <div class="row">
          <div v-for="(p, i) in products" :key="i" class="col-md-4">
            <div class="card p-3 m-3">
              <div class="card-header">{{ p.name }}</div>
              <div class="card-body">
                <img width="100%" :src="p.image" alt="" />
              </div>
              <div class="card-footer">
                <span>Price: <small>{{ p.price }} Ks</small></span>
                <a @click="addToCart(p)" 
                class="btn btn-sm btn-dark float-right">Add To Cart</a>
              </div>
            </div>
          </div>
        </div>
      </div>
    </Master>
  </template>
  
  <script>
  import Master from '../Layout/Master';
  import Loader from '../Component/Loader';
  import axios from 'axios';
  
  export default {
    components: { Master, Loader },
    name: "ProductPage",
    data() {
      return {
        isLoad: true,
        products: [],
      };
    },
    created() {
      axios.get('https://raw.githubusercontent.com/kominhtet/product.json/main/product.json')
        .then((res) => {
          console.log('Received data:', res.data);
          this.products = res.data;
          this.isLoad = false;
        })
        .catch((error) => {
          console.error('Error fetching data:', error);
          this.isLoad = false;
        });
    },
    methods:{
      addToCart(p){
        var cart = this.$root.cart;
        var isInCart = cart.find((v) => {
          return v.name == p.name;
        });
        if(isInCart){
          isInCart.qty++;
        }else{
          cart.push({...p,qty:1});
        }
        
      }
    }
  };
  </script>
  