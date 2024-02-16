<script setup>
  const emit = defineEmits(['start']);

  const startQuiz = () => {
    emit('start');
  }
</script>

<template>
  <section class="section__introduction">
    <h2 class="introduction__title">
      Descubra seu biotipo!
    </h2>

    <p class="introduction__description">
      Para que seu resultado seja assertivo, leia com calma todas as alternativas, e mesmo que fique em dúvida entre mais de uma, escolha  a que prevalecer de acordo com seu aspecto físico.
    </p>

    <button 
      class="introduction__button"
      @click="startQuiz"
    >
      Começar
    </button>

  </section>
</template>

<style src="./index.css" scoped/>