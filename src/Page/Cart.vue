<template>
  <Master>
    <div class="container">
      <table class="table table-striped">
        <thead>
          <tr>
            <th scope="col">Name</th>
            <th scope="col">Image</th>
            <th scope="col">+-</th>
            <th scope="col">Qty</th>
            <th scope="col">Price</th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="(p, i) in cart" :key="i">
            <td>{{ p.name }}</td>
            <td><img :src="p.image" width="15%" alt="" /></td>
            <td><span @click="addQty(p)" class="btn btn-sm btn-success">+</span>
              <span @click="reduceQty(p)" class="btn btn-sm btn-danger">-</span></td>
            <td>{{ p.qty }}</td>
            <td>{{ p.qty * p.price }}</td>
          </tr>
        </tbody>
      </table>
    </div>
  </Master>
</template>
<script>
import Master from '../Layout/Master';

export default {
  components: { Master },
  name: 'CartPage',
  data() {
    return {
      cart: [],
    };
  },
  created() {
    this.cart = this.$root.cart;
    console.log('Cart Data:', this.cart);
  },
  methods: {
    addQty(p) {
      p.qty++;
    },
    reduceQty(p) {
      p.qty--;
    },
  },
};
</script>
