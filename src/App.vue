<script setup>
import socksGreenImage from './assets/images/socks_green.jpeg';
import socksBlueImage from './assets/images/socks_blue.jpeg';
import { ref } from 'vue'

const product = ref('Socks');
const image = ref(socksGreenImage);
const url = ref("https://www.asics.com/ph/en-ph/unisexsocks08/green/?msockid=07a54cc5082364412d8d590a09be6523")

</script>

<template>
  <div class="product-display">
    <div class="product-container">
      <div class="product-image">
        <img :src="image" :href="url">
      </div>
      <div class="product-info">
        <h1>{{ product }}</h1>
      </div>
    </div>
  </div>
</template>