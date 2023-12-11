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

const menjarsComanda: Ref<Product[]> = ref([]);

function afegirMenjar(product: Product) {
  menjarsComanda.value.push(product);
  alert(menjarsComanda.value.map((product) => product.name));
}

function placeOrder() {
  alert('Your order has been placed!');
  menjarsComanda.value = [];
}
</script>

<template>
  <div class="principal">

    <h1>{{ nomComanda }}</h1>
    <input v-model="nomComanda" type="text" /><br>
    <button @click="placeOrder" type="button" class="separar">Place Order</button>
    <br>

    <Currency class="currency"></Currency>

    <ul>
    <li v-for="(product, index) in menjars" :key="index">
      <div class="centrar">
        <Comanda @@afegirProducteComanda="(product: Product) => afegirMenjar(product)" :info="product" />
      </div>
    </li>
  </ul>
  </div>
</template>

<style scoped>
.principal {
  text-align: center;
}

ul, li {
  list-style-type: none;
  text-align: center;
}

.separar {
  margin: 20px;
}

.centrar {
  display: flex;
  justify-content: center;
  align-items: center;
  width: 100%;
  height: 100%;
}
</style>