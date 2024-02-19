<script setup>
  import YouTube from 'vue3-youtube';

  const props = defineProps({
    biotype: {
      biotype: String,
      text: String,
      percentage: Number,
      video: String,
      pdf: String,
    }
  });

  const downloadPDF = () => {
    const pdfPath = `/pdfs/${props.biotype.pdf}`; 

    const urlPDF = new URL(pdfPath, import.meta.url).href;

    const link = document.createElement('a');
    
    link.href = urlPDF;
    link.download = props.biotype.pdf;
    link.click();
  }

</script>

<template>
  <section class="quiz-result">
    <div class="result-component">
      <div class="result-wrapper">
        <div class="biotype-wrapper">
          <h1 class="quiz-result__title">
            Você é
          </h1>

          <h3 class="first-biotype">
            {{ biotype.biotype }}!
          </h3>

          <p class="biotype-text">
            {{ biotype.text }}
          </p>

          <div class="video">
            <YouTube 
              width="100%" 
              :src="biotype.video" 
              ref="youtube"
            >
              Seu navegador não suporta o vídeo.
            </YouTube>
          </div>

          <p class="biotype-text">
            Baixe nosso material completo sobre o seu biotipo clicando no botão abaixo.
          </p>

          <button
            class="download__button" 
            @click="downloadPDF"
          >
            Download
          </button>
        </div>
      </div>
    </div>
  </section>
</template>

<style src="./index.css" scoped />