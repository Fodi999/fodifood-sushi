<script setup lang="ts">
import { ref } from 'vue';
import HeaderVue from './components/HeaderVue.vue';
import SiderVue from './components/SiderVue.vue';
import ContentVue from './components/ContentVue.vue';

import 'boxicons/css/boxicons.min.css'

const cart = ref<any[]>([]);

const addToCart = (product: any) => {
  cart.value.push(product);
};

const removeFromCart = (index: number) => {
  cart.value.splice(index, 1);
};
</script>

<template>
    <div>
      <HeaderVue/>
      <ContentVue @add-to-cart="addToCart" />
      <SiderVue :cart="cart" @remove-from-cart="removeFromCart"  /> 
    </div>
</template>