<script lang="ts">
import { defineComponent } from 'vue';

export default defineComponent({
  data() {
    return {
      products: [
        {
          name: 'Roll Fudzi',
          description: 'Skład: losos,kawior tobiko,krewetka, majonez,ser, ryż, nori',
          image: '/sait foto 8.png',
          price: 30, // цена
          weight: 250, // вес в граммах
          quantity: 8, // количество
          one: 1
        },
        {
          name: 'Big Momo',
          description: 'Skład: łosoś,papryka,awokado, ogorek, ryż, nori',
          image: '/sait foto 1.png',
          price: 35, // цена
          weight: 300, // вес в граммах
          quantity: 8, // количество
          one: 1
        },
        {
          name: 'Big Kanky',
          description: 'Skład: łosoś, papryka,awokado,ogorek, ser, ryż, nori',
          image: '/sait foto 2.png',
          price: 36, // цена
          weight: 340, // вес в граммах
          quantity: 8, // количество
          one: 1
        },
        {
          name: 'Big Oki',
          description: 'Skład: łosoś, krewetki, masago, ser, ryż, nori',
          image: '/sait foto 3.png',
          price: 35, // цена
          weight: 340, // вес в граммах
          quantity: 8, // количество
          one: 1
        },
        {
          name: 'Big Riku',
          description: 'Skład: łosoś, trądzik Unagi, ogorek, ser,ryż, nori',
          image: '/sait foto 4.png',
          price: 39, // цена
          weight: 340, // вес в граммах
          quantity: 8, // количество
          one: 1
        },
        {
          name: 'Big Kichi',
          description: 'Skład: łosoś, trądzik Unagi, tuńczyk, ser, ryż, nori',
          image: '/sait foto 5.png',
          price: 39, // цена
          weight: 350, // вес в граммах
          quantity: 8, // количество
          one: 1
        },
        {
          name: 'Big Zai',
          description: 'Skład: łosoś, wędzony łosoś, ser, ryż, nori',
          image: '/sait foto 6.png',
          price: 37, // цена
          weight: 330, // вес в граммах
          quantity: 8, // количество
          one: 1
        },
        {
          name: 'Roll Chuka',
          description: 'Skład: wodorosty chuka, sos orzechowy, sezam,ryż, nori',
          image: '/sait foto 7.png',
          price: 11, // цена
          weight: 130, // вес в граммах
          quantity: 8, // количество
          one: 1
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
          <div class="uppercase tracking-wide text-xl text-purple-900 font-bold">{{ product.name }}</div>
          <p class="mt-2 text-gray-500">{{ product.description }}</p>
        </div>
      </div>
      <div class="p-6 flex justify-between items-end">
        <p class="text-fuchsia-700 text-2xl font-bold">{{ product.price }} zl.</p>
        <div class="flex flex-col items-end">
          <p class="text-gray-500 mb-2">{{ product.weight }} gram. </p>
          <p class="text-gray-500 mb-2">{{ product.quantity }} szt.</p>
          <button @click="addToCart(product)" class="px-4 py-2 border border-transparent text-sm font-medium rounded-full text-white bg-gradient-to-r from-green-400 to-blue-500 hover:from-pink-500 hover:to-yellow-500 focus:outline-none focus:ring-2 focus:ring-offset-4 ">
            Kupić
          </button>
        </div>
      </div>
    </div>
  </div>
</template>