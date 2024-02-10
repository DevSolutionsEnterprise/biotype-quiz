<script setup>
import { ref, computed } from 'vue'
import YouTube from 'vue3-youtube'

const biotypeCounts = ref([
  {
    id: 0,
    biotype: 'ENDOMORFO',
    text: '',
    count: 0,
    video: ''
  },
  {
    id: 1,
    biotype: 'MESOMORFO',
    text: '',
    count: 0,
    video: ''  
  },
  {
    id: 2,
    biotype: 'ECTOMORFO',
    text: '',
    count: 0,
    video: ''
  }])

const biotypeQuestions = ref([
{
  question: 'Sua estrutura ossea é:',
  options: [{
    id: 0,
    biotype: 'ENDOMORFO',
    option: 'BEM LARGA'
  },
  {
    id: 1,
    biotype: 'MESOMORFO',
    option: 'LARGA E MÉDIA (normal)'
  },
  {
    id: 3,
    biotype: 'ECTOMORFO',
    option: 'PEQUENA e com aparencia frágil'
}],
  selected: null
},
{
  question: 'O seu corpo possui uma tendencia natural a:',
  options: [
  {
    id: 0,
    biotype: 'ENDOMORFO',
    option: 'Armazenar gordura'
  },
  {
    id: 1,
    biotype: 'MESOMORFO',
    option: 'Magro, porém com musculos visiveis '
  },
  {
    id: 2,
    biotype: 'ECTOMORFO',
    option: 'Sempre estar bem magro'
  }],
  selected: null
},
{
  question: 'Seu aspecto físico é:',
  options: [
  {
    id: 0,
    biotype: 'ENDOMORFO',
    option: 'Redondo e rechonchudo'
  },
  {
    id: 1,
    biotype: 'MESOMORFO',
    option: 'Quadrado e robusto'
  },
  {
    id: 2,
    biotype: 'ECTOMORFO',
    option: 'Longo e fino'
  }],
  selected: null
},
{
  question: 'Na sua opiniao, seus braços e pernas são:',
  options: [
  {
    id: 0,
    biotype: 'ENDOMORFO',
    option: 'Curtos e engrossados'
  },
  {
    id: 1,
    biotype: 'MESOMORFO',
    option: 'Possuem aspecto normal, com musculos visiveis'
  },
  {
    id: 2,
    biotype: 'ECTOMORFO',
    option: 'Longos e finos '
  }],
  selected: null
},
{
  question: 'Quando criança, voce era:',
  options: [
  {
    id: 0,
    biotype: 'ENDOMORFO',
    option: 'Gordinho / ganhava peso facil'
  },
  {
    id: 1,
    biotype: 'MESOMORFO',
    option: 'Normal'
  },
  {
    id: 2,
    biotype: 'ECTOMORFO',
    option: 'Magrinho '
  }],
  selected: null
},
{
  question: 'Seu metabolismo é:',
  options: [
  {
    id: 0,
    biotype: 'ENDOMORFO',
    option: 'Lento'
  },
  {
    id: 1,
    biotype: 'MESOMORFO',
    option: 'Normal'
  },
  {
    id: 2,
    biotype: 'ECTOMORFO',
    option: 'Muito rápido'
  }],
  selected: null
},
{
  question: 'Sobre seu peso, voce:',
  options: [
  {
    id: 0,
    biotype: 'ENDOMORFO',
    option: 'Ganha peso com facilidade, e tem dificuldade para perder'
  },
  {
    id: 1,
    biotype: 'MESOMORFO',
    option: 'Ganha peso ou perde facilmente, mas geralmente se mantem num peso ideal'
  },
  {
    id: 2,
    biotype: 'ECTOMORFO',
    option: 'Tem dificuldade para ganhar peso'
  }],
  selected: null
},
{
  question: 'Sobre seu apetite, voce sente fome:',
  options: [
  {
    id: 0,
    biotype: 'ENDOMORFO',
    option: 'Praticamente o dia todo'
  },
  {
    id: 1,
    biotype: 'MESOMORFO',
    option: 'Apetite controlado, sinto mais fome nos horarios das refeiçoes'
  },
  {
    id: 2,
    biotype: 'ECTOMORFO',
    option: 'Nao sinto muita fome'
  }],
  selected: null
},
{
  question: 'As pessoas falam que seu fisico aparenta:',
  options: [
  {
    id: 0,
    biotype: 'ENDOMORFO',
    option: 'Inchado, retido, grande, acima do peso'
  },
  {
    id: 1,
    biotype: 'MESOMORFO',
    option: 'Normal, porte atlético, nao precisa nem ganhar ou baixar peso'
  },
  {
    id: 2,
    biotype: 'ECTOMORFO',
    option: 'Magrelo, raquítico, abaixo do peso'
  }],
  selected: null
},
{
  question: 'Que tamanho de camiseta voce usa',
  options: [
  {
    id: 0,
    biotype: 'ENDOMORFO',
    option: 'G , GG, ou EXTRA G'
  },
  {
    id: 1,
    biotype: 'MESOMORFO ',
    option: 'M ou no máximo G'
  },
  {
    id: 2,
    biotype: 'ECTOMORFO',
    option: 'Geralmente P, às vezes M'
  }],
  selected: null
},
{
  question: 'Quando voce compra roupas, geralmente elas ficam:',
  options: [
  {
    id: 0,
    biotype: 'ENDOMORFO',
    option: 'Apertadas, preciso pegar tamanhos grandes para que nao fiquem desconfortáveis'
  },
  {
    id: 1,
    biotype: 'MESOMORFO',
    option: 'Normais e vestem bem'
  },
  {
    id: 2,
    biotype: 'ECTOMORFO',
    option: ' Largas, principalmente nos braços'
  }],
  selected: null
},
{
  question: 'Nesse momento, como voce descreve seu físico:',
  options: [
  {
    id: 0,
    biotype: 'ENDOMORFO',
    option: 'Estou acima do peso, quero perder gordura e definir '
  },
  {
    id: 1,
    biotype: 'MESOMORFO',
    option: 'Estou num peso ideal, porem quero mais definiçao'
  },
  {
    id: 2,
    biotype: 'ECTOMORFO',
    option: 'Estou abaixo do peso, quero ganhar volume muscular'
  }],
  selected: null
},
{
  question: 'Sua linha de cintura, naturalmente sempre foi:',
  options: [
  {
    id: 0,
    biotype: 'ENDOMORFO',
    option: 'Larga, grossa e redonda'
  },
  {
    id: 1,
    biotype: 'MESOMORFO',
    option: 'Normal'
  },
  {
    id: 2,
    biotype: 'ECTOMORFO',
    option: 'Pequena, fina'
  }],
  selected: null
}
])

const quizCompleted = ref(false)
const quizIntro = ref(true)
const currentQuestion = ref(0)

let biotypePercentage = []
let threeHighestPercentages = []
let optionSelected = null

const startQuiz = evt => {
  quizIntro.value = false
}

const getCurrentQuestion = computed(() => {
  let question = biotypeQuestions.value[currentQuestion.value]
  question.index = currentQuestion.value
  return question
})

const isFirtQuestion = computed(() => {
  if(getCurrentQuestion.value.index === 0) {
    return true
  }
  return false
})

const SetAnswer = evt => {
  biotypeQuestions.value[currentQuestion.value].selected = evt.target.value
  evt.target.value = null
}

const previusQuestion = () => {
  removeCount()
  currentQuestion.value--
}

const searchIdOptions = (indexQuestion, indexOption) => {
  return biotypeQuestions.value[indexQuestion]?.options[indexOption]?.id
}

const NextQuestion = () => {
  optionSelected = biotypeQuestions.value[currentQuestion.value].selected
  SetCount(searchIdOptions(currentQuestion.value, biotypeQuestions.value[currentQuestion.value].selected))
  if (currentQuestion.value < biotypeQuestions.value.length - 1) {
    currentQuestion.value++
  } else {
    quizCompleted.value = true
    setThreeHighestPercentages()
  }
}

const SetCount = (selectedOption) => {
  biotypeCounts.value.forEach(element => {
    if (element.id == selectedOption) {
      element.count++
    }
  });
}

const removeCount = () => {
  biotypeCounts.value.forEach(element => {
    if (element.id == optionSelected) {
      element.count--
    }
  });
}

const getThreeLargestObjects = (arr, property) => {
  arr.sort((a, b) => b[property] - a[property]);
  return arr.slice(0, 3);
}

const calcPercentage = (value) => {
  const percentage = (value/13) * 100
  return percentage
}

const setThreeHighestPercentages = () => {
  let i = 0
  biotypeCounts.value.forEach(element => {
    biotypePercentage[i] = {biotype: element.biotype, text: element.text, percentage: calcPercentage(element.count), video: element.video}
    // console.log('Obj: ', biotypePercentage[i])
    i++
  })
  threeHighestPercentages = getThreeLargestObjects(biotypePercentage, 'percentage')
  console.log('3maiores: ', threeHighestPercentages)
}
</script>

<template>
  <main class="app">
    <section 
      v-if="quizIntro"
      class="intro-section">
      <h1 class="intro-title">Qual é o seu <span class="intro-title-biotype">biotipo</span>?</h1>
      <p class="intro-text">
        Para que seu resultado seja assertivo, 
        leia com calma todas as alternativas, 
        e mesmo que fique em dúvida entre mais de uma,
        escolha a que prevalecer de4 acordo com seu aspecto físico.
      </p>
      <div class="intro-wrapper">
        <button 
          class="start-quiz-button"
          @click="startQuiz">
            Começar
          </button>
          <hr class="line">
      </div>
      <div class="img-wrapper">
        <img class="logo-img" src="./assets/images/prancheta_1_copia_14.png" alt="Logo">
      </div>
    </section>

    <section class="quiz" v-else-if="!quizCompleted && !quizIntro">
      <div class="quiz-info">
        <span class="question">{{ getCurrentQuestion.question }}</span>
      </div>
      <div class="options">
        <label 
          v-for="(option, index) in getCurrentQuestion.options" 
          :key="index"
          :class="`option ${
            getCurrentQuestion.selected == index
              ? 'selected'
              : ''
          }`">

          <input 
            type="radio" 
            :name="getCurrentQuestion.index"
            :value="index"
            v-model="getCurrentQuestion.selected"
            @change="SetAnswer">
            <span>{{ option.option }}</span>
        </label>
      </div>

      <div class="wrapper-button">
        <button
          v-if="!isFirtQuestion"
          class="return-button"
          @click="previusQuestion"
        >
        Voltar
        </button>
        <button
          class="next-button"
          @click="NextQuestion"
          :disabled="!getCurrentQuestion.selected">
          {{ 
            getCurrentQuestion.index == biotypeQuestions.length - 1
              ? 'Finalizar'
              : getCurrentQuestion.selected == null
                ? 'Selecione uma opção'
                : 'Avançar'
          }}
        </button>
      </div>
    </section>
    
    <section v-else>
      <h1 class="final-title"><span class="congrats">Parabéns!</span> Analisei os dados do seu perfil e aqui abaixo estão os arquétipos que mais combinam com você! </h1>
      <div class="result-component">
        <div class="result-wrapper">
          <div class="biotype-wrapper">
            <p class="first-biotype">{{ threeHighestPercentages[0].biotype }}: {{ parseInt(threeHighestPercentages[0].percentage) }}%</p>
            <p class="biotype-text">{{ threeHighestPercentages[0].text }}</p>
            <div class="video">
              <YouTube width="100%" :src="threeHighestPercentages[0].video" ref="youtube">
                Seu navegador não suporta o vídeo.
              </YouTube>
            </div>
          </div>
          <div class="biotype-wrapper" v-if="threeHighestPercentages[1].percentage">
            <p class="second-biotype">{{ threeHighestPercentages[1].biotype }}: {{ parseInt(threeHighestPercentages[1].percentage) }}%</p>
            <p class="biotype-text">{{ threeHighestPercentages[1].text }}</p>
          </div>
          <div class="biotype-wrapper-last" v-if="threeHighestPercentages[2].percentage">
            <p class="third-biotype">{{ threeHighestPercentages[2].biotype }}: {{ parseInt(threeHighestPercentages[2].percentage) }}%</p>
            <p class="biotype-text">{{ threeHighestPercentages[2].text }}</p>
          </div>
        </div>
        <div>
          <p class="access-first-info">Para ter acesso às aulas de todos os arquétipos, basta entrar em sua área de membros.</p>
          <a 
            class="access-button" 
            target="_blank"
            href="https://sso.hotmart.com/login?service=https://purchase.hotmart.com/?_gl=1*1chgn4f*_ga*MTQwNzEyNDQ1OC4xNjc2NjQwODk5*_ga_GQH2V1F11Q*MTY3NjczNDQ3Ni41LjEuMTY3NjczNTM3Ny41Ny4wLjA.&renew=true"
          >
            Acessar
          </a>
          <p class="access-second-info">Ao acessá-la, o próximo passo será assistir o módulo “Aulas de aplicação” para saber como usar seus principais arquétipos de forma prática em suas redes sociais e demais lugares.</p>
          <p class="msg">Boas aulas!</p>
        </div>
      </div>
    </section>
  </main>
</template>

<style>
@font-face {
  font-family: 'Brown Sugar';
  src: url('../src/assets/fonts/Brown_Sugar.otf') format('truetype');
}

@font-face {
  font-family: 'Claster Oleander';
  src: url('../src/assets/fonts/Claster_Oleander.otf') format('truetype');
}

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body {
  background-image: url('./assets/images/img-noise-361x370.png');
  background-repeat: repeat;
}

.app {
  display: flex;
  flex-direction: column;
  padding: 2rem;
  min-height: 100vh;
}

h1 {
  font-weight: 2rem;
  margin-bottom: 2rem;
}

.intro-title {
  font-family: 'Claster Oleander';
  font-weight: 500;
  font-size: 6em;
  color: #227382;
  margin: 40px 0;
}

.intro-title-biotype {
  font-family: 'Brown Sugar';
  color: #C5A361;
}

.intro-text {
  font-family: 'Poppins', sans-serif;
  font-weight: 500;
  font-size: 1.5em;
  color: #585858;
}

.attention {
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  
}

.intro-wrapper {
  display: flex;
  margin-top: 70px;
}

.start-quiz-button {
  appearance: none;
  outline: none;
  border: none;
  cursor: pointer;

  background-image: linear-gradient(to right, #C5A361, #DFC694);
  border-radius: 8px;
  font-size: 1.3em;
  font-weight: 500;
  font-family: 'Claster Oleander';
  padding: 15px 55px;
  color: #000;
}

.start-quiz-button:hover {
  opacity: 80%;
}

.line {
  border: 1% solid black;
  width: 100%;
  height: 0;
  margin: 20px 0 20px 50px;
}

.img-wrapper {
  display: flex;
  justify-content: left;
  margin-top: 50px;
}

.logo-img {
  width: 180px;
  height: auto;
  opacity: 70%;
}

.quiz {
  background-color: #C9BCB3;
  padding: 1rem;
  width: 100%;
  max-width: 640px;
  border-radius: 0.5rem;
  align-self: center;
  flex-wrap: wrap;
}

.quiz-info {
  display: flex;
  justify-content: space-between;
  margin-bottom: 1rem;
}

.quiz-info .question {
  color: black;
  font-size: 2rem;
  font-family: 'Claster Oleander';
}

.quiz-info .score {
  color: #FFF;
  font-size: 1.25rem;
}

.options {
  margin-bottom: 1rem;
}

.option {
  display: block;
  padding: 1rem;
  color: #E6D9D9;
  background-color: #227382;
  margin-bottom: 0.5rem;
  border-radius: 0.5rem;
  cursor: pointer;
  font-family: 'Poppins', sans-serif;
}

.option:hover {
  background-color: #DFC694;
  color: #000;
}

.option.correct {
 background-color: #2cce7d;
}

.option.wrong {
  background-color: #ff5a5f;
}

.option.selected {
  color: #000;
 background-color: #C5A361;
}

.option:last-of-type {
  margin-bottom: 0;
}

.option.disabled {
  opacity: 0.5;
}

.option input {
  display: none;
}

.wrapper-button {
  text-align: right;
}

.return-button, .next-button  {
  appearance: none;
  outline: none;
  border: none;
  cursor: pointer;

  padding: 0.5rem 1rem;
  background-image: linear-gradient(to right, #C5A361, #DFC694);
  color: #2d213f;
  border-radius: 8px;
  font-size: 1.3em;
  font-weight: 500;
  font-family: 'Claster Oleander';
}

.return-button {
  float: left;
}

.final-title {
  font-family: 'Claster Oleander';
  font-weight: 500;
  font-size: 3em;
  color: #227382;
  margin: 10px 0 50px 0;
  text-align: center;
}

.congrats {
  color: #C5A361; 
  font-family: 'Brown Sugar';
}

.result-component {
  background-color: #C9BCB3;
  border-radius: 0.5rem;
  padding: 1.5rem;
}

.result-wrapper {
  background-color: #227382;
  border-radius: 0.5rem;
  padding: 20px 10px;
  box-shadow: 0 0 20px #868584;
}

.biotype-wrapper {
  margin-bottom: 70px;
  text-align: center;
}
.biotype-wrapper-last {
  text-align: center;
  margin-bottom: 5px;
}

.first-biotype, .second-biotype, .third-biotype {
  font-family: 'Claster Oleander';
  
  font-weight: 600;
  color: #C5A361;
  margin-bottom: 10px;
}

.first-biotype, .second-biotype, .third-biotype {
  font-size: 3em;
}

.video {
  margin: 20px auto 0 auto;
  max-width: 640px;
  max-height: 360px;
}

.biotype-text {
  color: #DFC694;
  font-size: 1.5em;
  font-family: 'Poppins', sans-serif;
}

.access-button {
  appearance: none;
  outline: none;
  border: none;
  cursor: pointer;

  background-image: linear-gradient(to right, #C5A361, #DFC694);
  border-radius: 8px;
  font-size: 1.3em;
  font-weight: 500;
  font-family: 'Claster Oleander';
  padding: 15px 55px;
  color: #000;
  display: block;
  margin: 0 auto;
  text-align: center;
  width: 200px;
  text-decoration: none;
}

.access-button:hover {
  opacity: 80%;
}

.access-first-info, .access-second-info {
  text-align: center;
  margin: 20px 0;
}

.access-first-info {
  font-size: 2.5em;
  font-family: 'Claster Oleander';
  color: #227382;
  margin-top: 50px;
}

.access-second-info {
  font-family: 'Poppins', sans-serif;
  color: #585858;
  font-size: 1.5em;
}

.msg {
  color: #C5A361;
  text-align: center;
  font-family: 'Brown Sugar';
  font-weight: 700;
  font-size: 4em;
  margin: 20px 0; 
}

button:disabled {
  opacity: 0.5;
}

h2 {
  font-size: 2rem;
  margin-bottom: 2rem;
  text-align: center;
}

p {
  color: #8f8f8f;
  font-size: 1.25rem;
}

@media screen and (max-width: 970px) {
  .intro-title {
    font-size: 5em;
  }

}

@media screen and (max-width: 820px) {
  .intro-title {
    font-size: 4em;
  }
}

@media screen and (max-width: 434px) {
  .first-biotype, .second-biotype, .third-biotype {
    font-size: 2em;
  }
  .biotype-text {
    font-size: 1em;
  }
}

@media screen and (max-width: 669px) {
  .intro-title {
    font-size: 3em;
  }
}

@media screen and (max-width: 560px) {
  .intro-title {
    text-align: center;
    margin-top: 20px;
  }
  .intro-text {
    font-size: 1.2em;
    text-align: center;
  }
  .intro-wrapper {
    margin-top: 40px;
  }
  .img-wrapper {
    justify-content: center;
  }
  .logo-img {
    width: 120px;
  }
  .start-quiz-button {
    display: block;
    margin: 0 auto;
    text-align: center;
  }
  .line {
    display: none;
  }
}

@media screen and (max-width: 373px) {
  .return-button, .next-button {
    font-size: 0.9em;
  }
}
</style>
