<script setup>
  import Header from './components/Header/index.vue';
  import Quiz from './views/Quiz/index.vue';
  import Footer from './components/Footer/index.vue';
  
</script>

<template>
  <Header />

  <main class="app">
    <Quiz />
  </main>

  <Footer class="footer"/>
</template>

<style src="./App.css" />
