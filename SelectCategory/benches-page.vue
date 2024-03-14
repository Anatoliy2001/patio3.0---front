<template>     <div class="products-catalog">
  <!-- <div>
    <h1>Store</h1>
    <div v-for="item of items" :key="item.id">
      <p>{{ item.name }}</p>
      <button @click="removeFromCart(item.id)" v-if="isInCart(item.id)">
        remove from cart
      </button>
      <button @click="addToCart(item.id)" v-else>add to cart</button>
    </div>
    <button @click="$router.push('/cart')">check out</button>
  </div> -->
  <div v-for="item of items" v-bind:key="item.componentKey" class="product">
  <div class="card" style="width: 80%;">
     <img :src="getImgUrl(item.imageUrl)" class="card-img-top" alt="..." id="img4">
     <div class="card-body">
       <h5 class="card-title">{{ item.name }}</h5>
       <p class="card-text">{{ item.desc }}</p>
       
       <div class="button-container"> 

        <button @click="addToCart(item.id)" class="all-buttons add-button">{{ $t('button1') }}</button>
        <button @click="removeFromCart(index)" class="all-buttons remove-button">
          {{ $t('button2') }}
                </button>
       </div>
     </div>
</div>
</div>


</div>

</template>
 
<script>

import i18n from '../../i18n';

export default {
  name: 'benches-page',
  data() {
    return {
      items: ([
  {
    id: 1,

    imageUrl: "benches/aurora/1.jpg",
    name: i18n.global.t('benches1'),
    desc: i18n.global.t('benches2'),
    componentKey: 0
  
  },
  {
    id: 2,

    imageUrl: "benches/forest/1.jpg",
    name: i18n.global.t('benches3'),
    desc: i18n.global.t('benches4'),
    componentKey: 0
  },
  {
    id: 3,

    imageUrl: "benches/monaco/1.jpg",
    name: i18n.global.t('benches5'),
    desc: i18n.global.t('benches6'),
    componentKey: 0
  },
  {
    id: 4,

    imageUrl: "benches/peterhof/1.jpg",
    name: i18n.global.t('benches7'),
    desc: i18n.global.t('benches8'),
    componentKey: 0
  },
  {
  id: 5,

    imageUrl: "benches/versal/1.jpg",
    name: i18n.global.t('benches9'),
    desc: i18n.global.t('benches10'),
    componentKey: 0
  },
]),
      cart: [],
      IsOpen: false,
    };
  },
  methods: {
    getImgUrl(pic) {
  return require('../../assets/' + pic);
    },
    isInCart(itemId) {
      if (!localStorage.getItem("cart")) {
        localStorage.setItem("cart", JSON.stringify([]));
      }
      const cartItem = this.cart.find(({ id }) => id === itemId);
      return Boolean(cartItem);
    },
    addToCart(itemId) {
      this.hui=true
      const item = this.items.find(({ id }) => id === itemId);
 
      if (!localStorage.getItem("cart")) {
        localStorage.setItem("cart", JSON.stringify([]));
      }
      const cartItems = JSON.parse(localStorage.getItem("cart"));


   
        this.isInCart(itemId)
      
      cartItems.push(item);
      localStorage.setItem("cart", JSON.stringify(cartItems));
      console.log(this.cart);
      this.isInCart(itemId)
    },
    removeFromCart(itemId) {

      const cartItems = JSON.parse(localStorage.getItem("cart"));
      const index = cartItems.findIndex(({ id }) => id === itemId);
      cartItems.splice(index, 1);
      localStorage.setItem("cart", JSON.stringify(cartItems));
      this.cart = JSON.parse(localStorage.getItem("cart"));
      this.isInCart(itemId)
      console.log(this.cart);
      
    },
    getCart() {
      if (!localStorage.getItem("cart")) {
        localStorage.setItem("cart", JSON.stringify([]));
      }
      this.cart = JSON.parse(localStorage.getItem("cart"));
      
    }
}
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>