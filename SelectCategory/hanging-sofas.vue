<template>
  <div class="products-catalog">
    <div v-for="item of items" :key="item.id" track-by='number' class="product">
      <div class="card" style="width: 80%;">
        <img :src="getImgUrl(item.imageUrl)" class="card-img-top" alt="..." id="img4">
        <div class="card-body">
          <h5 class="card-title">{{ item.name }}</h5>
          <p class="card-text">{{ item.desc }}</p>
          
          <div class="button-container"> 

            <button @click="addToCart(item.id)" class="all-buttons add-button">{{ $t('button1') }}</button>
          
            <button @click="removeFromCart(index, item.id)"  class="all-buttons remove-button">
              {{ $t('button2') }}
                    </button>
               
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
 
<script>

import { Navigation, Pagination, Scrollbar, A11y } from "swiper/modules";
// Import Swiper Vue.js components
// Import Swiper styles
import "swiper/css";
import "swiper/css/navigation";
import "swiper/css/pagination";
import "swiper/css/scrollbar";

export default {
  name: 'hanging-page',
  data() {
    return {
      items: [{
                id: 13,
                number: 0,
                imageUrl: "sofas/monaco/1.jpg",
                name: 'THE "MONACO" MODEL',
                desc: 'A model in a classic modern style. We can do it in any size within 1x2 m.'
              },
              {
                id: 14,
                number: 0,
                // imageUrl: "sofas/provence/1.jpg",
                imageUrl: "sofas/provence/1.jpg",
                name: 'THE "PROVENCE" MODEL',
                desc: 'An elegant model will decorate your veranda or terrace. We can do it in any size within 1x2 m.'
              },
              {
                id: 15,
                number: 0,
                // imageUrl: "sofas/versal/1.jpg",
                imageUrl: "sofas/versal/1.jpg",
                name: 'THE "VERSAILLES" MODEL',
                desc: 'An elegant model will decorate your veranda or terrace. We can do it in any size within 1x2 m.'
              },
              {
                id: 16,
                number: 0,
                // imageUrl: "sofas/domino/1.jpg",
                imageUrl: "sofas/domino/1.jpg",
                name: 'THE "DOMINO" MODEL',
                desc: 'An interesting model with a back and a seat made of domino cubes. Any size in dimensions of 1,8x0,7 m. Textiles are optional.'
              },
              ],
      cart: [],
      hui: false
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
    removeFromCart(itemId, ) {
      const cartItems = JSON.parse(localStorage.getItem("cart"));
      const index = cartItems.findIndex(({ id }) => id === itemId);
      cartItems.splice(index, 1);
      localStorage.setItem("cart", JSON.stringify(cartItems));
      this.cart = JSON.parse(localStorage.getItem("cart"));
      this.isInCart(itemId)

      
    },
    getCart() {
      if (!localStorage.getItem("cart")) {
        localStorage.setItem("cart", JSON.stringify([]));
      }
      this.cart = JSON.parse(localStorage.getItem("cart"));
      
    },


  },
  beforeMount() {
    this.getCart();
  },
  mounted() {
    this.getCart()
    if(localStorage.Number) this.Number = localStorage.Number;
    },
    watch:{
    Num(newNum) {
      localStorage.Number = newNum;
    }
  },
  setup() {
    const onSwiper = (swiper) => {
      console.log(swiper);
    };
    const onSlideChange = () => {
    };
    return {
      onSwiper,
      onSlideChange,
      modules: [Navigation, Pagination, Scrollbar, A11y],
    };
  },
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.swip {
  border-radius: 0.2vmin;
  height: 42vmin;
  background-position: center center;
  background-repeat: no-repeat;
  object-fit:cover;
  width: 80%;
}
.bestswip {
  z-index: 19999998;
  margin-top: 0vmin;
  width: 100%;
}
</style>