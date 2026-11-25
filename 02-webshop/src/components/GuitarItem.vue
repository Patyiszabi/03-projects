<script setup>
import { useCartStore } from '../store/cart.js'
import GuitarDescr from './GuitarDescr.vue';
import GuitarImage from './GuitarImage.vue';
import GuitarTitle from './GuitarTitle.vue';

defineProps({
  guitar: {
    type: Object,
    required: true
  }
})

const { addToCart } = useCartStore()
</script>

<template>
  <li class="guitar">
    <GuitarImage :title="guitar.title" />
    <GuitarTitle :title="guitar.title" />
    <GuitarDescr  :description="guitar.description" />
    <p>
      <strong>${{ guitar.price }}</strong> · Rating: {{ guitar.rating }}/5 ·
      {{ guitar.stock > 0 ? `${guitar.stock} in stock` : 'Out of stock' }}
    </p>
    <button :disabled="guitar.stock <= 0" @click="addToCart(guitar)">Add to cart</button>
  </li>
</template>

<style scoped>
.guitar {
  border: 1px solid #ddd;
  border-radius: 8px;
  padding: 1rem;
}
</style>
