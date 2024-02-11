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
      <span class="congrats">
        Parabéns!
      </span> 

      Analisei os dados do seu perfil e aqui abaixo estão os arquétipos que mais combinam com você! 
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
          Para ter acesso às aulas de todos os arquétipos, basta entrar em sua área de membros.
        </p>

        <a 
          class="access-button" 
          target="_blank"
          href="https://sso.hotmart.com/login?service=https://purchase.hotmart.com/?_gl=1*1chgn4f*_ga*MTQwNzEyNDQ1OC4xNjc2NjQwODk5*_ga_GQH2V1F11Q*MTY3NjczNDQ3Ni41LjEuMTY3NjczNTM3Ny41Ny4wLjA.&renew=true"
        >
          Acessar
        </a>

        <p class="access-second-info">
          Ao acessá-la, o próximo passo será assistir o módulo “Aulas de aplicação” para saber como usar seus principais arquétipos de forma prática em suas redes sociais e demais lugares.
        </p>

        <p class="msg">
          Boas aulas!
        </p>
      </div>
    </div>
  </section>
</template>

<style src="./index.css" scoped />