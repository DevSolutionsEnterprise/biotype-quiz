<script setup>
import { ref, computed, onUpdated } from 'vue'

const archetypeCounts = ref([{
    id: 0,
    archetype: 'Governante',
    count: 0
  },
  {
    id: 1,
    archetype: 'Criador',
    count: 0  
  },
  {
    id: 2,
    archetype: 'Cuidador',
    count: 0
  },
  {
    id: 3,
    archetype: 'Herói:',
    count: 0
  },
  {
    id: 4,
    archetype: 'Rebelde',
    count: 0
  },
  {
    id: 5,
    archetype: 'Sábio',
    count: 0
  },
  {
    id: 6,
    archetype: 'Explorador',
    count: 0
  },
  {
    id: 7,
    archetype: 'Inocente',
    count: 0
  },
  {
    id: 8,
    archetype: 'Cara Comum',
    count: 0
  },
  {
    id: 9,
    archetype: 'Bobo da corte',
    count: 0
  },
  {
    id: 10,
    archetype: 'Mago',
    count: 0
  },
  {
    id: 11,
    archetype: 'Amante',
    count: 0
  }])

const archetypeQuestions = ref([{
  question: 'Sobre a sua personalidade, qual desses traços está mais presente em você?',
  options: [{
    id: 0,
    archetype: 'Governante',
    option: 'Ambicioso'
  },
  {
    id: 1,
    archetype: 'Criador',
    option: 'Criativo'
  },
  {
    id: 2,
    archetype: 'Cuidador',
    option: 'Amoroso/Cuidadoso'
  },
  {
    id: 3,
    archetype: 'Herói:',
    option: 'Forte/Resiliente'
  },
  {
    id: 4,
    archetype: 'Rebelde',
    option: 'Questionador/Revolucionário'
  },
  {
    id: 5,
    archetype: 'Sábio',
    option: 'Reflexivo/Estudioso/Sábio'
  },
  {
    id: 6,
    archetype: 'Explorador',
    option: 'Aventureiro/Viajante'
  },
  {
    id: 7,
    archetype: 'Inocente',
    option: 'Sonhador/Idealizador'
  },
  {
    id: 8,
    archetype: 'Cara Comum',
    option: 'Empático/Amigável'
  },
  {
    id: 9,
    archetype: 'Bobo da corte',
    option: 'Engraçado/Divertido'
  },
  {
    id: 10,
    archetype: 'Mago',
    option: 'Esperitual/Inspirador'
  },
  {
    id: 11,
    archetype: 'Amante',
    option: 'Romântico'
  }],
  selected: null
},
{
  question: 'Seus principais valores:',
  options: [
  {
    id: 0,
    archetype: 'Governante',
    option: 'Liderança, autoridade, ordem, controle, luxo, sucesso, poder.'
  },
  {
    id: 1,
    archetype: 'Criador',
    option: 'Criatividade, curiosidade, integridade, inovação, imaginação.'
  },
  {
    id: 2,
    archetype: 'Cuidador',
    option: 'Cuidado, compaixão, acolhimento, altruísmo'
  },
  {
    id: 3,
    archetype: 'Herói:',
    option: 'Coragem, ação, motivação, superação, disciplina'
  },
  {
    id: 4,
    archetype: 'Rebelde',
    option: 'Disrupção, quebra de padrões, questionamento, originalidade, revolução'
  },
  {
    id: 5,
    archetype: 'Sábio',
    option: 'Conhecimento, aprendizagem, lógica, razão, verdade.'
  },
  {
    id: 6,
    archetype: 'Explorador',
    option: 'Liberdade, independência, dinamismo, aventura, natureza'
  },
  {
    id: 7,
    archetype: 'Inocente',
    option: 'Otimismo, esperança, simplicidade, bondade, pureza, felicidade.'
  },
  {
    id: 8,
    archetype: 'Cara Comum',
    option: 'Inclusão, igualdade, pertencimento, comunidade, amizade.'
  },
  {
    id: 9,
    archetype: 'Bobo da corte',
    option: 'Alegria, diversão, bom humor, leveza'
  },
  {
    id: 10,
    archetype: 'Mago',
    option: 'Inspiração, encantamento, magia, experiência, intuição, transformação, consciência.'
  },
  {
    id: 11,
    archetype: 'Amante',
    option: 'Beleza, paixão, atração, relacionamento, desejo, sedução'
  }],
  selected: null
},
{
  question: 'Seu AMBIENTE preferido é um lugar:',
  options: [{
    id: 0,
    archetype: 'Governante',
    option: 'Ambicioso'
  },
  {
    id: 1,
    archetype: 'Criador',
    option: 'Criativo'
  },
  {
    id: 2,
    archetype: 'Cuidador',
    option: 'Amoroso/Cuidadoso'
  },
  {
    id: 3,
    archetype: 'Herói:',
    option: 'Forte/Resiliente'
  },
  {
    id: 4,
    archetype: 'Rebelde',
    option: 'Questionador/Revolucionário'
  },
  {
    id: 5,
    archetype: 'Sábio',
    option: 'Reflexivo/Estudioso/Sábio'
  },
  {
    id: 6,
    archetype: 'Explorador',
    option: 'Aventureiro/Viajante'
  },
  {
    id: 7,
    archetype: 'Inocente',
    option: 'Sonhador/Idealizador'
  },
  {
    id: 8,
    archetype: 'Cara Comum',
    option: 'Empático/Amigável'
  },
  {
    id: 9,
    archetype: 'Bobo da corte',
    option: 'Engraçado/Divertido'
  },
  {
    id: 10,
    archetype: 'Mago',
    option: 'Esperitual/Inspirador'
  },
  {
    id: 11,
    archetype: 'Amante',
    option: 'Romântico'
  }],
  selected: null
},
{
  question: 'Teste:',
  options: [{
    id: 0,
    archetype: 'Governante',
    option: 'Chique, caro e luxuoso, que transmita poder e autoridade'
  },
  {
    id: 1,
    archetype: 'Criador',
    option: 'Que me dê inspiração para criar'
  },
  {
    id: 2,
    archetype: 'Cuidador',
    option: 'Confortável, aconchegante, acolhedor'
  },
  {
    id: 3,
    archetype: 'Teste:',
    option: 'Testando'
  }],
  selected: null
}])

const quizCompleted = ref(false)
const quizIntro = ref(true)
const currentQuestion = ref(0)

let archetypePercentage = []
let threeHighestPercentages = []


const stratQuiz = evt => {
  quizIntro.value = false
}

const getCurrentQuestion = computed(() => {
  let question = archetypeQuestions.value[currentQuestion.value]
  question.index = currentQuestion.value
  return question
})

const SetAnswer = evt => {
  archetypeQuestions.value[currentQuestion.value].selected = evt.target.value
  evt.target.value = null
  console.log('Selecionadio: ', archetypeQuestions.value[currentQuestion.value].selected)
  SetCount(archetypeQuestions.value[currentQuestion.value].selected)
}

const NextQuestion = () => {
  if (currentQuestion.value < archetypeQuestions.value.length - 1) {
    currentQuestion.value++
  } else {
    quizCompleted.value = true
    setThreeHighestPercentages()
  }
}

const SetCount = (selectedOption) => {
  archetypeCounts.value.forEach(element => {
    if (element.id == selectedOption) {
      // console.log('id: ', element.id, 'anterior: ', element.count)
      element.count++
      // console.log('id: ', element.id, 'atual: ', element.count)
    }
  });
}

const getThreeLargestObjects = (arr, property) => {
  arr.sort((a, b) => b[property] - a[property]);
  console.log('entrou')
  return arr.slice(0, 3);
}

const calcPercentage = (value) => {
  const percentage = (value/4) * 100
  return percentage
}

const setThreeHighestPercentages = () => {
  let i = 0
  archetypeCounts.value.forEach(element => {
    archetypePercentage[i] = {achertype: element.archetype, percentage: calcPercentage(element.count)}
    i++
  })
  threeHighestPercentages = getThreeLargestObjects(archetypePercentage, 'percentage')
  console.log('archetypePercentage: ', archetypePercentage)
  console.log('threeHighestPercentages: ', threeHighestPercentages)
}


</script>

<template>
  <main class="app">
    <section 
      v-if="quizIntro"
      class="intro-section">
      <h1 class="intro-title">Qual é o seu arquétipo?</h1>
      <!-- <div class="attention">
        <span class="attention-text">ATENÇÃO!</span>
        <span class="attention-text">
          Para que seu resultado seja assertivo, 
          leia com calma todas as alternativas, 
          e mesmo que fique em dúvida entre mais de uma, 
          escolha a que prevalecer em sua personalidade ou aspecto do seu negócio.
        </span> 
      </div> -->
      <div class="intro-wrapper">
        <button 
          class="start-quiz-button"
          @click="stratQuiz">
            Começar
          </button>
          <hr class="line">
      </div>
    </section>

    <section class="quiz" v-else-if="!quizCompleted && !quizIntro">
      <div class="quiz-info">
        <span class="question">{{ getCurrentQuestion.question }}</span>
        <!-- <span class="score">Score {{ getCurrentQuestion.value }}/{{ archetypeQuestions.length }}</span> -->
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

      <button
        class="next-question-button"
        @click="NextQuestion"
        :disabled="!getCurrentQuestion.selected">
        {{ 
          getCurrentQuestion.index == archetypeQuestions.length - 1
            ? 'Finalizar'
            : getCurrentQuestion.selected == null
              ? 'Selecione uma opção'
              : 'Avançar'
        }}
      </button>
    </section>
    
    <section v-else>
      <h1 class="final-title">Conheça seus arquétipos</h1>
      <div>
        <p class="first-archetype">{{ threeHighestPercentages[0].achertype }}: {{ threeHighestPercentages[0].percentage }}%</p>
        <p class="second-archetype">{{ threeHighestPercentages[1].achertype }}: {{ threeHighestPercentages[1].percentage }}%</p>
        <p class="third-archetype">{{ threeHighestPercentages[2].achertype }}: {{ threeHighestPercentages[2].percentage }}%</p>
      </div>
    </section>
  </main>
</template>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body {
  background-color: #e6d9d9;
  color: #FFF;
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

.intro-section {
  margin-top: 60px;
}

.intro-title {
  max-width: 60%;
  font-family: 'Claster Oleander';
  font-weight: 500;
  font-size: 6em;
  color: #227382;
  margin-bottom: 70px;
}

.attention {
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  
}

.attention-text {
  color: #C5A361;
}

.intro-wrapper {
  display: flex;
}

.start-quiz-button {
  appearance: none;
  outline: none;
  border: none;
  cursor: pointer;

  background-image: linear-gradient(to right, #C5A361, #DFC694);
  border-radius: 8px;
  font-size: 1.1em;
  font-weight: 500;
  font-family: 'Claster Oleander';
  cursor: pointer;
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
  background-color: #227382;
  margin-bottom: 0.5rem;
  border-radius: 0.5rem;
  cursor: pointer;
  font-family: 'Poppins';
}

.option:hover {
  background-color: #DFC694;
}

.option.correct {
 background-color: #2cce7d;
}

.option.wrong {
  background-color: #ff5a5f;
}

.option.selected {
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

.next-question-button {
  appearance: none;
  outline: none;
  border: none;
  cursor: pointer;

  padding: 0.5rem 1rem;
  background-image: linear-gradient(to right, #C5A361, #DFC694);
  color: #2d213f;
  border-radius: 8px;
  font-size: 1.1em;
  font-weight: 500;
  font-family: 'Claster Oleander';
}

.next-question-button:hover {
}

.final-title {
  font-family: 'Claster Oleander';
  font-weight: 500;
  font-size: 6em;
  color: #227382;
  margin-bottom: 70px;
  text-align: center;
}
.first-archetype {
  font-family: 'Claster Oleander';
  font-weight: 500;
  font-size: 3em;
  color: #227382;
  margin-bottom: 70px;
}
.second-archetype {
  font-family: 'Claster Oleander';
  font-weight: 500;
  font-size: 2em;
  color: #227382;
  margin-bottom: 70px;
}

.third-archetype {
  font-family: 'Claster Oleander';
  font-weight: 500;
  font-size: 1.75em;
  color: #227382;
  margin-bottom: 70px;
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
  text-align: center;
}






</style>
