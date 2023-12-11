<template>
    <span>Currency</span>
    <select name="currency" id="money" @change="selectCurrency">
      <option value="euro">Euros(€)</option>
      <option value="dollar">Dollars($)</option>
    </select>
  </template>
  
  <script setup>
  import { ref } from 'vue';
  
  const selectedCurrency = ref('euro'); // Valor inicial por defecto
  
  function selectCurrency(event) {
    selectedCurrency.value = event.target.value;
    emit('currencyChanged', selectedCurrency.value);
  }
  </script>