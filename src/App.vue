<template>
  <div class="container">
    <div class="row">
      <div class="col-md-7">
        <div class="row">
          <div class="col-md-6" v-for="product in products" v-bind:key="product.id">
            <Product :isInCart="isInCart(product)" v-on:add-to-cart="addToCart(product)" :product="product"></Product>
          </div>
        </div>
      </div>
      <div class="col-md-5">
        <cart v-on:pay-now="pay()" :items="cart" v-on:remove-from-cart="removeItem($event)"></cart>

      </div>
    </div>
  </div>
</template>

<script>
import products from "@/products.json";
import Product from "@/components/Product.vue";
import Cart from "@/components/Cart.vue";

export default {
  name: "app",

   components: {

    Product,

    Cart

  },

  data() {
    return{

      products,

      cart: [],

      adding: false

    }
   
  },

  methods: {

    addToCart(product){
      // console.log(product);
      this.adding = true;
      this.cart.push(product);
      this.adding = false  
    },

    isInCart(product){

      const item = this.cart.find(item => item.id === product.id)

      if(item){

        return true

      }

        return false
    
    },

    removeItem(product){

      this.cart = this.cart.filter(item => item.id !== product.id)

    },

    pay(){

      alert('Shopping Completed');
      
    }
  }


};
</script>

<style>
body {
  background-color: aquamarine;
}
</style>
