<script setup>
import { ref, watch } from 'vue'
import socksGreenImage from './assets/images/socks_green.jpeg'
import socksBlueImage from './assets/images/socks_blue.jpeg'

const product = ref('Socks')
const inStock = true
  
const details = ref(['50% cotton', '30% wool', '20% polyester'])

const variants = ref([
  { id: 2234, color: 'green', image: socksGreenImage },
  { id: 2235, color: 'blue', image: socksBlueImage },
])

const selectedVariant = ref(0)
const image = ref(variants.value[selectedVariant.value].image)

const cart = ref(0)

watch(selectedVariant, (newIndex) => {
  image.value = variants.value[newIndex].image;
})

const addToCart = () => {
  if(inStock === true) {
    cart.value += 1
  }
} ;

const updateImage = (index) => {
  selectedVariant.value = index
}

</script>
  
<template>
  <div class="nav-bar"></div>
  <div class="cart">Cart({{ cart }})</div>
  <div class="product-display">
    <div class="product-container">
      <div class="product-image">    
        <img v-bind:src="image">
      </div>
      <div class="product-info">
        <h1>{{ product }}</h1>
        <p v-if="inStock">In Stock</p>
        <p v-else>Out of Stock</p>
        <ul>
          <li v-for="detail in details">{{ detail }}</li>
        </ul>
        <div v-for="(variant, index) in variants" 
          :key="variant.id"
          @mouseover="updateImage(index)"
          class="color-circle"
          :class="{ active: selectedVariant === index }"
          :style="{ backgroundColor: variant.color  }"
        >
        </div>
        <button 
        class="button" 
        :class="{disabledButton: !inStock}"
        v-on:click="addToCart">Add to cart</button>
      </div>
    </div>
  </div>
</template>