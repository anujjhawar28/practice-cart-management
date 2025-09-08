<script setup lang="ts">
import CartItem from "./CartItem.vue";
import type {PropType} from "vue";
import { CartType } from "./types";

defineProps({
  items: {
    type: Array as PropType<CartType[]>
  },
  tax: Number,
  grandTotal: Number,
  subTotal: Number
})

defineEmits(['update-qty', 'remove-item'])
</script>

<template>
  <div class="cart">
    <h2>Your Cart</h2>
    <div v-if="items.length === 0" class="empty">Cart is empty</div>
    <CartItem v-for="(cart, index) in items" :key="index" :item="cart"
      @update-qty="$emit('update-qty', cart.id, $event)" @remove-item="$emit('remove-item', cart.id)" />

    <div class="totals">
      <p>Subtotal: ${{subTotal}}</p>
      <p>Tax (10%): ${{tax.toFixed(2)}}</p>
      <h3>Grand Total: ${{grandTotal.toFixed(2)}}</h3>
    </div>
  </div>
</template>

<style scoped>
.cart {
  flex: 1;
  border: 1px solid #ddd;
  padding: 10px;
  border-radius: 5px;
  background-color: #fff;
  padding-bottom: 15px;
}
.empty{ 
  text-align: center;
}

.totals {
  margin-top: 15px;
  border-top: 1px solid #ddd;
  padding-top: 10px;
}
</style>