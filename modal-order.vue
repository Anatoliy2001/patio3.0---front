<template>
  <div class="wrapper">
    <Modal
      v-model:visible="isVisible"
      title="YOUR ORDER"
      type="clean"
      zIndex="999999999999999999"
    >
      <div class="cart-menu">
        <div class="cart-head">
          <h4>{{ $t("cart1") }}</h4>
        </div>
        <form action="mail.php" method="POST">
          <div class="cart-in">
            <div>
              <div v-for="(c, index) of cart" :key="c.number">
                <p>{{ c.name }}</p>
                
                <img :src="getImgUrl(c.imageUrl)" />
                <button @click="removeFromCart(index); c.number = 0" class="remove-button">
                  REMOVE
                </button>

              </div>
            </div>
          </div>

          <div class="cart-body">
            <input type="hidden" id="smth" name="cart" value=" " />

            <div class="input-container">
              <input type="text" required="" name="fullName" />
              <label>{{ $t("cart2") }}</label>
            </div>
            <div class="input-container">
              <input type="mail" required="" name="email" />
              <label>{{ $t("cart3") }}</label>
            </div>
            <div class="input-container">
              <input type="tel" required="" name="phone" />
              <label>{{ $t("cart4") }}</label>
            </div>
            <button class="btn btn-dark" type="submit">
              {{ $t("cart5") }}
            </button>
          </div>
        </form>
      </div>
    </Modal>
    <div class="cart-trigger" @click="(isVisible = true), getCart()" id="waffel">
      <span class="lnr lnr-cart"></span>
    </div>
  </div>
</template>
<script>
import { ref } from "vue";
import { Modal } from "usemodal-vue3";
// import router from '../router'
export default {
  name: "modal-order",
  components: {
    Modal,
  },
  data() {
    return { isVisible: ref(false),
      IsOpen: false,
       cart: [],

    items: ([
  {
    IsOpen: false
  }
]) };
  },
  methods: {
    getImgUrl(pic) {
  return require('../assets/' + pic);
    },
    removeFromCart(itemId) {
      const cartItems = JSON.parse(localStorage.getItem("cart"));
      const index = cartItems.findIndex(({ id }) => id === itemId);
      cartItems.splice(index, 1);
      localStorage.setItem("cart", JSON.stringify(cartItems));
      this.cart = JSON.parse(localStorage.getItem("cart"));
      this.items.IsOpen = true
      cartItems.push(this.items);

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
};
</script>
<style scoped>
.remove-button {
  border-radius: 1.2vmin;
  color: #fff;
  background-color: rgb(245, 48, 48);
  border: none;
  padding: 1vmin;
  font-weight: 500;
  margin-top: 1.5vmin;
}
.modal-vue3-content {
  width: 100%;
}
.plys {
  border:none;
  margin: 1vmin;
}
.menus {
  margin: 1vmin;
  border:none;
}
</style>
