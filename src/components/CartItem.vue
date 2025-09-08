<script setup lang="ts">
import type { PropType } from 'vue'
import { CartType } from './types';

defineProps({
  item: {
    type: Object as PropType<CartType>
  }
})

defineEmits(['update-qty', 'remove-item'])
</script>

<template>
  <div class="cart-item">
    <span>{{item.name}}</span>
    <input type="number" min="1" :value="item.qty" @input="$emit('update-qty', Number($event.target.value))" />
    <button class="delete" @click="$emit('remove-item')">X</button>
  </div>
</template>

<style scoped>
.cart-item {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin: 5px 0px;
}

input {
  width: 50px;
  text-align: center;
}

button.delete {
  background-color: red;
  color: white;
  cursor: pointer;
  border: none;
  border-radius: 4px;
  padding: 4px 8px;
}

button:hover {
  background-color: darkred;
}
</style>