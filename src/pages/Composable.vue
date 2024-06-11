<template>
  <div class="container flex flex-col items-center gap-5 my-20">
    <h1 class="text-red-500 text-5xl">Composable</h1>
    <div>
      <h2 class="text-green-500 text-5xl">Products</h2>
      <div class="grid grid-cols-4 gap-5">
        <div
          class="bg-gray-100/50 p-5 rounded"
          v-for="product in products"
          :key="product.id"
        >
          <img :src="product.thumbnail" alt="" />

          <h1 class="text-2xl font-medium line-clamp-1 my-3">
            {{ product.title }}
          </h1>
          <p class="line-clamp-2 mb-3">{{ product.description }}</p>
          <h1 class="text-2xl font-medium">{{ product.price }} $</h1>
        </div>
        </div>
        </div>
      <Loading v-if="loading" />
    <button @click="test" class="bg-blue-500 p-2 text-white rounded-xl">leadMore</button>
  </div>
</template>

<script setup>
import Loading from "../components/Loading.vue";
import { useProducts } from "../composable/useProducts";

const { products, loading, fetchProducts } = useProducts();

fetchProducts();
const test = () => {
  fetchProducts();
};
</script>

<style lang="scss" scoped></style>
