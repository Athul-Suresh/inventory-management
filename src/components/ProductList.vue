<template>
  <div>
    <h1>Products list</h1>

    <ul>
      <li v-for="product in products" :key="product?.id">{{ product?.name }}</li>
    </ul>
  </div>
</template>

<script setup>
import axios from 'axios'
import { onMounted, ref } from 'vue'

const products = ref([])

onMounted(() => {
  fetchProducts()
})

const fetchProducts = () => {
  axios
    .get('http://127.0.0.1:8000/api/products')
    .then((response) => {
      products.value = response.data.data
    })
    .catch((error) => console.log(error))
}
</script>
