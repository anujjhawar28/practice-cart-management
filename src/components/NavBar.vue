<script setup>
defineProps({
  cartCount: Number
})
</script>

<template>
  <div class="navbar">
    <h1>My Shop</h1>
    <div class="cart-badge">
      Cart: <span>{{cartCount}}</span>
    </div>
  </div>
</template>

<style scoped>
.navbar {
  background-color: #0077cc;
  color: white;
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 10px 20px;
}

.cart-badge span {
  background-color: white;
  color: #0077cc;
  padding: 2px 5px;
  border-radius: 5px;
  font-weight: bold;
}
</style>