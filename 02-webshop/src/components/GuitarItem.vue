<script setup>
import { useCartStore } from '../store/cart.js'
import GuitarImage from './GuitarImage.vue';

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
    <p>{{ guitar.description }}</p>
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
