<script setup lang="ts">
import { ref, type Ref, reactive } from "vue";
import Currency from "@/components/Currency.vue"
import type Product from "./types/Product.ts";
import Comanda from "./components/Comanda.vue";
const nomComanda = ref('');
const menjars = reactive([
  { name: "Hamburger 🍔", price: 5 },
  { name: "Cheeseburger 🧀", price: 6 },
  { name: "Impossible Burger 🥕", price: 7 },
  { name: "Fries 🍟", price: 2 },
]);

const cart: Ref<Product[]> = ref([]);

// const afegirMenjar = (product: Product): void => {
//   cart.value.push(product);
//   alert(cart.value.map((product) => product.name));
// };

function afegirMenjar(product: Product) {
  cart.value.push(product);
  alert(cart.value.map((product) => product.name));
}


const placeOrder = (): void => {
  alert(`Your order has been placed.`);
};

</script>

<template>
  <header>
    <h1>{{ nomComanda }}</h1>
    <section>
      <input v-model="nomComanda" type="text" />
      <button @click="placeOrder" type="button">Place Order</button>
    </section>
  </header>

  <Currency></Currency>

    <section class="productes">
      <Comanda
        @@add-to-cart="(product:Product) => afegirMenjar(product)"
        v-for="(product, index) in menjars"
        :info="product"
        :key="index"
      />
    </section>
</template>