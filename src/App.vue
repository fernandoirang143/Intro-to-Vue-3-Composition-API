<script setup> /* composition API style in Vue 3*/
import { ref } from 'vue'
import socksGreenImage from './assets/images/socks_green.jpeg'

const product = ref('Socks')
const image = ref(socksGreenImage)
const inStock = true
var details = ref(['50% cotton', '30% wool', '20% polyester']);
const variants = ref([
  {id: 2234, color: 'green', size: 'xs'},
  {id: 2235, color: 'blue', size: 'l'}
]);

var sizes = ref(['XS', 'S', 'M', 'L', 'XL']);
var newSize = ref('');
function addItem() {
  if(newSize.value.trim() !== '') {
    sizes.value.push(newSize.value);
    newSize.value = '';
  }
}

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
        <p v-if="inStock">In Stock</p>
        <p v-else>Out of Stock</p>
        <ul>
          <li v-for="detail in details">{{ detail }}</li>
        </ul>
        <ul>
          <li v-for="(variant, index) in variants">{{ index + 1 + ". " + variant.color + " " + variant.size }}</li>
        </ul>
        <input type="text" v-model="newSize" placeholder="Enter a new size">
        <button @click="addItem">Add item</button>
        <ul>
          <li v-for="size in sizes">{{ size }}</li>
        </ul>
      </div>
    </div>
  </div>
</template>