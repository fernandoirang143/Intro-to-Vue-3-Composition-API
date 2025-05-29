<script setup>
 import {ref} from 'Vue';
 const product = ref('Socks');
 const description = ref('These are great socks!')
</script>

<template>
  <div class="product-display">
    <div class="product-container">
      <div class="product-info">
        <h1>{{ product }}</h1>
        <p>{{ description }}</p>
      </div>
    </div>
  </div>
</template>