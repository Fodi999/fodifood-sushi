<script lang="ts">
import { ref, defineComponent } from 'vue';

interface CartItem {
  name: string;
  image: string;
  description: string;
  price: number; // цена
  weight: number; // вес в граммах
  quantity: number; // количество
}

export default defineComponent({
  props: {
    cart: {
      type: Array as () => CartItem[],
      required: true
    }
  },
  
    computed: {
  total() {
    return this.cart.reduce((total: number, item: CartItem) => total + item.price, 0);
  }
},
  setup(props, { emit }) {
    const isOpen = ref(false);

    const openSider = () => {
      isOpen.value = true;
    };

    const closeSider = () => {
      isOpen.value = false;
    };

    const removeFromCart = (index: number) => {
      emit('remove-from-cart', index);
    };

    return {
      isOpen,
      openSider,
      closeSider,
      removeFromCart
    };
  }
});
</script>

<template>
  <div>
    <button @click="openSider" class="px-2 py-2 bg-blue-500 text-white rounded fixed bottom-0  right-0 m-3 text-sm">Открыть корзину</button>
    <div :class="{ 'translate-x-0': isOpen, '-translate-x-full': !isOpen }" class="fixed top-0 right-0 h-full w-96 bg-gray-200 transform transition-transform duration-200 ease-in-out overflow-auto space-y-4 p-4 z-50">
      <button @click="closeSider" class="px-2 py-1  rounded-full text-sm">
        <i class=' transform rotate-180 text-3xl bx bx-right-arrow-circle' style='color:#ff0040'  ></i></button>
      
      <div v-for="(item, index) in cart" :key="index" class="my-2 mx-1 ml-2 mr-2 bg-white rounded-lg shadow-md flex md:flex-row  transform transition duration-500 ease-in-out hover:scale-105">
  <div class="md:flex-shrink-0">
    <img class="h-32 w-full object-cover object-left md:w-32 rounded-t-lg" :src="item.image" alt="Product image">
  </div>
  <div class="p-4 pr-4 flex-grow flex flex-col justify-between">
    <div>
      <div class="uppercase tracking-wide text-xs text-indigo-500 font-semibold">{{ item.name }}</div>
      <p class="mt-1 text-gray-500 text-xs">{{ item.description }}</p>
      <p class="mt-1 text-gray-500 text-xs">Вес: {{ item.weight }} г</p>
      <p class="mt-1 text-gray-500 text-xs">Количество: {{ item.quantity }}</p>
      <p class="mt-1 text-gray-500 text-xs">Цена: {{ item.price }} zl.</p>
    </div>
    <button @click="removeFromCart(index)" class="mt-2 px-2 py-1 border border-transparent text-xs font-medium rounded-md text-white bg-indigo-600 hover:bg-indigo-700 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-indigo-500 self-end">
      Remove
    </button>
  </div>
</div>
<div class="bottom-0 w-full p-4 rounded-t-xl bg-sky-700">
  <div class="flex items-center justify-between">
    <span>Итого:</span>
    <div class="flex-1 border-dashed border-b-2 border-black mb-6"></div>
    <span class="font-bold">{{ total }} zl.</span>
  </div>
  <div class="mt-4">
    <button class="bg-blue-500 w-full rounded-xl text-sm font-bold hover:bg-blue-700">
      Zamówienie
    </button>
  </div>
</div>
      </div>
      
      </div>
  
    
</template>
<style>
.translate-x-0 {
  transform: translateX(0);
}
.-translate-x-full {
  transform: translateX(100%);
}
</style>
  
 