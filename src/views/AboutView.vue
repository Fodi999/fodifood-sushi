<script>
export default {
  props: {
    orderTotal: {
      type: Number,
      required: true,
    },
  },
  data() {

    return {
      name: '',
      phone: '',

    }
  },
  
  methods: {
    goToMessenger() {
      window.open('https://m.me/102194024947729', '_blank');
    },
  },
}
</script>
<template>
  
  <div class="flex flex-col">
        <label class="mb-2">Сумма заказа</label>
        <p class="border-2 border-gray-300 p-2 rounded-md">{{ orderTotal }}</p>
      </div>
  <div class="flex justify-center items-center min-h-screen">
    <div class="w-96 flex flex-col space-y-4">
      <div class="flex flex-col">
        <label for="name" class="mb-2">Имя</label>
        <input id="name" v-model="name" type="text" class="border-2 border-gray-300 p-2 rounded-md" placeholder="Введите ваше имя">
      </div>
      <div class="flex flex-col">
        <label for="phone" class="mb-2">Телефон</label>
        <input id="phone" v-model="phone" type="text" class="border-2 border-gray-300 p-2 rounded-md" placeholder="Введите ваш номер телефона">
      </div>
      <div class="flex flex-col">
        
        
        <button @click="goToMessenger" class="bg-blue-500 text-white p-2 rounded-md mt-2">Перейти в Messenger</button>
      </div>
      <button @click="submitForm" class="bg-blue-500 text-white p-2 rounded-md">Связаться</button>
    </div>
    <router-link to="/" class="bg-blue-500 text-white p-2 rounded-md fixed bottom-4 right-4">Вернуться на главную</router-link>
  </div>
</template>
  



