<template>
  <div class="container">
    <Header/>
    <RouterView/>
    <Footer/>
  </div>
</template>

<script setup>
import Header from '@/components/Layout/Header.vue'
import Footer from '@/components/Layout/Footer.vue'
</script>



<style lang="scss">
@import url('https://fonts.cdnfonts.com/css/clash-display');
@import "./assets/styles/global.scss";


</style>
