<script setup>
  const emit = defineEmits(['start']);

  const startQuiz = () => {
    emit('start');
  }
</script>

<template>
  <section class="intro-section">
    <h1 class="intro-title">
      Qual é o seu 
      <span class="intro-title-biotype">biotipo</span>?
    </h1>

    <p class="intro-text">
      Para que seu resultado seja assertivo, 
      leia com calma todas as alternativas, 
      e mesmo que fique em dúvida entre mais de uma,
      escolha a que prevalecer de acordo com seu aspecto físico.
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

    <div class="img-wrapper">
      <img 
        class="logo-img" 
        src="./assets/images/prancheta_1_copia_14.png" 
        alt="Logo"
      />
    </div>
  </section>
</template>

<style src="./index.css" scoped/>