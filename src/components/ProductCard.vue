<script setup>
const props = defineProps({
  product: Object
})

defineEmits(['add-to-cart'])
</script>

<template>
  <div class="product-card">
    <img :src="product.image" class="image" />
    <h3>{{product.name}}</h3>
    <p>${{product.price}}</p>
    <button @click="$emit('add-to-cart')">Add to Cart</button>
  </div>
</template>

<style scoped>
.product-card {
  border: 1px solid #ddd;
  padding: 10px;
  border-radius: 5px;
  text-align: center;
  background-color: #fafafa;
}

button {
  margin-top: 8px;
  background-color: #0077cc;
  color: white;
  border: none;
  cursor: pointer;
  padding: 5px 10px;
  border-radius: 4px;
}

button:hover {
  background-color: #005fa3;
}

.image {
  height: 60px;
  width: 60px;
}
</style>