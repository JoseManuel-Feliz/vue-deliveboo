<template>
  <div>
    <nav class="navbar navbar-expand-lg navbar-light bg-light">
      <div class="container-fluid">
        <a class="navbar-brand" href="/">DeliveBoo</a>
        <div class="cart-icon" @click="toggleCart">
          <img src="https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcSUO7WZsrUlz6XT-6-e07YnghUoF6r-9w_0tQ&s"
            alt="Carrello" class="icon" />
          <!-- Usa cartCount dal CartStore -->
          <span v-if="cartCount > 0" class="cart-badge">{{ cartCount }}</span>
        </div>
      </div>
    </nav>
    <router-view />
  </div>
</template>

<script>
import { useCartStore } from '../stores/cartStore';

export default {
  name: 'AppHeader',
  methods: {
    toggleCart() {
      this.$emit('toggle-cart');
    },
  },
  computed: {
    cartCount() {
      const cartStore = useCartStore(); // Accedi al CartStore
      return cartStore.totalItem; // Usa il getter `cartCount`
    },
  },
};
</script>


<style>
.icon {
  height: 30px;
  cursor: pointer;
  position: relative;
}

.cart-badge {
  position: absolute;
  top: 3px;
  right: 5px;
  background-color: red;
  color: white;
  border-radius: 50%;
  padding: 4px;
  font-size: 10px;
  font-weight: bold;
}
</style>
