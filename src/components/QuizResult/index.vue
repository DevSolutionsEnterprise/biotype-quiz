<script setup>
  import YouTube from 'vue3-youtube';

  defineProps({
    biotype: {
      biotype: String,
      text: String,
      percentage: Number,
      video: String,
    }
  });

  const downloadPdf = () => {
    const pdfUrl = '/caminho/do/seu/arquivo.pdf';
      window.open(pdfUrl, '_blank');
  }

</script>

<template>
  <section>
    <h1 class="final-title">
      Parabéns!! Seu biotipo é:
    </h1>

    <div class="result-component">
      <div class="result-wrapper">
        <div class="biotype-wrapper">
          <p class="first-biotype">
            "{{ biotype.biotype }}"
          </p>

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
          <button class="download__button" @click="downloadPdf">Download</button>
        </div>
      </div>
    </div>
  </section>
</template>

<style src="./index.css" scoped />