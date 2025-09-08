<script setup>
import ProductCard from "./ProductCard.vue";
import {ref, computed} from "vue"

const props = defineProps({
  products: {
    type: Array,
    default: () => []
  }
})

const emit = defineEmits(['add-to-cart'])

const file = ref()
const search = ref("")

const filterProducts = computed(() => {
  if(!search.value.trim()) return props.products
  return props.products.filter(p => p.name.toLowerCase().includes(search.value.toLowerCase()))
})
</script>

<template>
  <div class="product-list">
      <input v-model="search" placeholder="Search products..." class="search-bar" type="text"/>
    <div class="grid">
      <ProductCard 
        v-for="(product, index) in filterProducts" 
        :key="index" 
        :product="product"
        @add-to-cart="$emit('add-to-cart', product)" />
    </div>
  </div>
</template>

<style scoped>
.product-list {
  flex: 2;
}

.grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 15px;
}
.search-bar {
  width: 100%;
  padding: 5px 10px;
  margin-bottom: 15px;
  border: 1px solid #ccc;
  border-radius: 5px;
}
</style>