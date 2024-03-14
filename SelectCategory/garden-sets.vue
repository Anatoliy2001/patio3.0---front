<template>
        <div class="products-catalog">  
            <div v-for="item of items" :key="item.desc" class="product">
  <div class="card" style="width: 80%;">
     <img :src="this.path" class="card-img-top" alt="..." id="img4">
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
import axios from 'axios';
export default {
  name: 'garden-sets',
  data() {
    return {
      path: '',
      cart: [],
      items: ([
  {
    id: 6,
    imageUrl: "garden/aurora/1.jpg",
    name: i18n.global.t('sets1'),
    desc: i18n.global.t('sets2')
  },
])
    };
  },
  methods: {
    
    getImgUrl() {
      axios.get('http://localhost:3000/files')
        .then(response => {
          const fileArray = response.data.files;
          console.log(fileArray);
          console.log(fileArray[0].path.replaceAll("'", ''));
          console.log(typeof fileArray[0].path.replaceAll("'", ''))
          this.path = fileArray[0].path.replaceAll("'", '');
          //this.path = 'http://localhost:8080/img/first.2b90e807.jpg'
        })
        .catch(error => {
          console.error('Error:', error);
        });
      return (this.path);
    },
    isInCart(itemId) {
      if (!localStorage.getItem("cart")) {
        localStorage.setItem("cart", JSON.stringify([]));
      }
      const cartItem = this.cart.find(({ id }) => id === itemId);
      return Boolean(cartItem);
    },
    addToCart(itemId) {
      const item = this.items.find(({ id }) => id === itemId);
      if (!localStorage.getItem("cart")) {
        localStorage.setItem("cart", JSON.stringify([]));
      }
      const cartItems = JSON.parse(localStorage.getItem("cart"));
     
        this.isInCart(itemId)
      
      cartItems.push(item);
      localStorage.setItem("cart", JSON.stringify(cartItems));
   
      //items.push({ number: item.number++ });
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
      
    },



  },
  mounted() {
    this.getCart(),
    this.getImgUrl()

    },
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>