<script setup>
import { ref } from 'vue'
import socksGreenImage from './assets/images/socks_green.jpeg'

const product = ref('Socks')
const image = ref(socksGreenImage)
const inStock = ref(true);
const inventory = ref(100);
const onSale = ref(true);

</script>
  
<template>
  <div class="nav-bar"></div>
  <div class="product-display">
    <div class="product-container">
      <div class="product-image">    
        <img v-bind:src="image">
      </div>
      <div class="product-info">
        <h1>{{ product }}</h1>
        <p v-show="onSale && inventory != 0">On Sale</p>
        <p v-if="inventory > 10"> In Stock</p> <!-- or with v-show when false the display:none -->
        <p v-else-if="inventory <= 10 && inventory > 0"> Almost sold out!</p>
        <p v-else>Out of Stock</p>
      </div>
    </div>
  </div>
</template>