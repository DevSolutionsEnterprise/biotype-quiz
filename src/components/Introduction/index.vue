<script setup>
  const emit = defineEmits(['start']);

  const startQuiz = () => {
    emit('start');
  }
</script>

<template>
  <section class="intro-section">
    <h2 class="intro-title">
      TESTE DE BIOTIPO
    </h2>

    <p class="intro-text">
      Para que seu resultado seja assertivo, leia com calma todas as alternativas e mesmo que fique em dúvida entre mais de uma, escolha a que prevalecer em sua aparência física e de acordo com o que as pessoas comentam para você sobre seu corpo.
    </p>

    <div class="intro-wrapper">
      <button 
        class="start-quiz-button"
        @click="startQuiz"
      >
        Começar
      </button>

      <hr class="line">
    </div>

  </section>
</template>

<style src="./index.css" scoped/>