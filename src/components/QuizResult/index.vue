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
</script>

<template>
  <section>
    <h1 class="final-title">
        Você é
    </h1>

    <div class="result-component">
      <div class="result-wrapper">
        <div class="biotype-wrapper">
          <p class="first-biotype">
            {{ biotype.biotype }}
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
        </div>
      </div>

      <div>
        <p class="access-first-info">
          Lorem Ipsum is simply dummy text of the printing and typesetting industry.
        </p>

        <a 
          class="access-button" 
          target="_blank"
        >
          Acessar
        </a>

        <p class="access-second-info">
          Lorem Ipsum is simply dummy text of the printing and typesetting industry.
        </p>

        <p class="msg">
          Lorem Ipsum!
        </p>
      </div>
    </div>
  </section>
</template>

<style src="./index.css" scoped />