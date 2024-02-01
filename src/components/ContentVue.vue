<script lang="ts">
import { defineComponent } from 'vue';

export default defineComponent({
  data() {
    return {
      products: [
        {
          name: 'Product name',
          description: 'Product description goes here. This is a simple description of the product.',
          image: '/public/Banzai.jpg',
          price: 100, // цена
          weight: 500, // вес в граммах
          quantity: 8 // количество
        },
        {
          name: 'Big Momo',
          description: 'Skład: łosoś,papryka,awokado, ogorek, ryż, nori',
          image: '/public/sait foto 1.png',
          price: 35, // цена
          weight: 300, // вес в граммах
          quantity: 8 // количество
        },
        {
          name: 'Product name',
          description: 'Product description goes here. This is a simple description of the product.',
          image: '/public/Banzai.jpg',
          price: 100, // цена
          weight: 500, // вес в граммах
          quantity: 8 // количество
        },
        {
          name: 'Product name',
          description: 'Product description goes here. This is a simple description of the product.',
          image: '/public/Banzai.jpg',
          price: 100, // цена
          weight: 500, // вес в граммах
          quantity: 8 // количество
        },
        {
          name: 'Product name',
          description: 'Product description goes here. This is a simple description of the product.',
          image: '/public/Banzai.jpg',
          price: 100, // цена
          weight: 500, // вес в граммах
          quantity: 8 // количество
        },
        {
          name: 'Product name',
          description: 'Product description goes here. This is a simple description of the product.',
          image: '/public/Banzai.jpg',
          price: 100, // цена
          weight: 500, // вес в граммах
          quantity: 8 // количество
        },
        {
          name: 'Product name',
          description: 'Product description goes here. This is a simple description of the product.',
          image: '/public/Banzai.jpg',
          price: 100, // цена
          weight: 500, // вес в граммах
          quantity: 8 // количество
        },
        {
          name: 'Product name',
          description: 'Product description goes here. This is a simple description of the product.',
          image: '/public/Banzai.jpg',
          price: 100, // цена
          weight: 500, // вес в граммах
          quantity: 8 // количество
        },
        // добавьте здесь больше продуктов по аналогии
      ]
    }
  },
  methods: {
    addToCart(product: any) {
      this.$emit('add-to-cart', product);
    }
  },
  emits: ['add-to-cart'] // добавьте это
});
</script>


<template>
  <div class="grid grid-cols-1 sm:grid-cols-2 md:grid-cols-3 lg:grid-cols-4 gap-4 mt-20">
    <div v-for="product in products" :key="product.name" class="max-w-sm mx-auto bg-white rounded-xl shadow-md overflow-hidden md:max-w-md m-3 flex flex-col justify-between  transform transition duration-500 ease-in-out hover:scale-105">
      <div>
        <img class="h-48 w-full object-contain" :src="product.image" alt="Product image">
        <div class="p-6">
          <div class="uppercase tracking-wide text-sm text-indigo-500 font-semibold">{{ product.name }}</div>
          <p class="mt-2 text-gray-500">{{ product.description }}</p>
        </div>
      </div>
      <div class="p-6 flex justify-between items-end">
        <p class="text-gray-500 text-2xl font-bold">{{ product.price }} zl.</p>
        <div class="flex flex-col items-end">
          <p class="text-gray-500 mb-2">{{ product.weight }} gram. </p>
          <p class="text-gray-500 mb-2">{{ product.quantity }} szt.</p>
          <button @click="addToCart(product)" class="px-4 py-2 border border-transparent text-sm font-medium rounded-md text-white bg-indigo-600 hover:bg-indigo-700 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-indigo-500">
            Buy
          </button>
        </div>
      </div>
    </div>
  </div>
</template>