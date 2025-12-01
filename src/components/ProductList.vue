<template>
  <div>
    <h1 class="text-2xl text-black underline">Products list</h1>

    <div>
      <div
        class="max-w-sm rounded overflow-hidden shadow-lg"
        v-for="product in products"
        :key="product?.id"
      >
        <div class="px-6 py-4">
          <div class="font-bold text-xl mb-2">{{ product?.name }}</div>
          <p class="text-gray-700 text-base">
            {{ product?.description }}
          </p>
          <button @click="updateProduct" class="border rounded p-1 bg-orange-500">Edit</button>
        </div>
      </div>
    </div>

    <button class="border rounded bg-blue-500 mt-5 p-1" @click="updateStock">Update Stock</button>
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

const updateStock = () => {}
const updateProduct = () => {}
</script>
