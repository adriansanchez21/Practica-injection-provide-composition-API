<script setup lang="ts">
import type Product from "../types/Product.ts";
defineProps<{
  info: Product;
}>();

defineEmits<{
  "@addToCart": [info: Product];
}>();
</script>

<template>
  <article>
    <p>{{ info.name }}</p>
    <p>{{ info.price }}</p>
    <CurrencyPrice :price="info.price" />
    <button @click="$emit('@addToCart', info)" type="button">
      Add to Cart
    </button>
  </article>
</template>