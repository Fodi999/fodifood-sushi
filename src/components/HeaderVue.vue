<script>
export default {
  data() {
    return {
      isScrolled: false,
    };
  },
  methods: {
    checkScroll() {
      this.isScrolled = window.scrollY > 200;
    },
    scrollToTop() {
      window.scrollTo({ top: 0, behavior: 'smooth' });
    },
  },
  created() {
    window.addEventListener('scroll', this.checkScroll);
  },

};
</script>
<template>
    <header className="fixed top-0 z-10 left-0 right-0 flex border-b-4 border-black justify-between items-center p-6 bg-gradient-to-r from-indigo-500 via-purple-500 to-pink-500">
      
  <div>
    <button v-show="isScrolled" @click="scrollToTop"><h1 className="bg-gradient-to-r from-green-400 to-blue-500 hover:from-pink-500 hover:to-yellow-500 underline uppercase font-bold text-2xl">FoDifood</h1></button>
  </div>
  <div className="flex space-x-4">
    <a href="https://facebook.com" target="_blank" rel="noreferrer" className="text-white">
      <i className='bx bxl-facebook-circle text-xl'></i>
    </a>
    <a href="https://instagram.com " target="_blank" rel="noreferrer" className="text-white">
      <i className='bx bxl-instagram text-xl'></i> 
    </a>
    <a href=" " target="_blank" rel="noreferrer" className="text-white">
      <i className='bx bx-globe text-xl'></i>
    </a>
  </div>
</header>
  </template>
  
  