<script setup>
  import { ref, computed } from 'vue';

  import Introduction from '../../components/Introduction/index.vue';
  import Quiz from '../../components/Quiz/index.vue';
  import QuizResult from '../../components/QuizResult/index.vue';

  import { QUESTIONS } from '../../constants/questions';

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
    }
  ]);

  const biotypeQuestions = ref(QUESTIONS);

  const quizCompleted = ref(false);
  const quizIntro = ref(true);
  const currentQuestion = ref(0);
  const definedBiotype = ref({});

  let optionSelected = null;

  const FIRST_INDEX_QUESTION = 0;
  const QUANTITY_COUNT_INITIAL = 0;
  const NAME_BIOTYPE_PERCENT = 'percentage';

  const startQuiz = () => {
    quizIntro.value = false
  }

  const getCurrentQuestion = computed(() => {
    let question = biotypeQuestions.value[currentQuestion.value];

    question.index = currentQuestion.value;

    return question
  })

  const isFirstQuestion = computed(() => {
    if (getCurrentQuestion.value.index === FIRST_INDEX_QUESTION) {
      return true;
    }

    return false;
  })

  const setAnswer = indexQuestion => {
    biotypeQuestions.value[currentQuestion.value].selected = indexQuestion;
  }

  const previousQuestion = () => {
    removeCount();

    currentQuestion.value--;
  }

  const nextQuestion = () => {
    optionSelected = biotypeQuestions.value[currentQuestion.value].selected;

    setCount(searchIdOptions(currentQuestion.value, biotypeQuestions.value[currentQuestion.value].selected));

    if (currentQuestion.value < biotypeQuestions.value.length - 1) {
      currentQuestion.value++;
    } else {
      quizCompleted.value = true;

      setThreeHighestPercentages();
    }
  }

  const searchIdOptions = (indexQuestion, indexOption) => {
    return biotypeQuestions.value[indexQuestion]?.options[indexOption]?.id;
  }  

  const setCount = (selectedOption) => {
    biotypeCounts.value.forEach(element => {
      if (element.id == selectedOption) {
        element.count++
      }
    });
  }

  const removeCount = () => {
    biotypeCounts.value.forEach(element => {
      if (element.id === optionSelected) {
        element.count--;
      }
    });
  }

  const getHighestPercent = (biotypes) => {
    const newBiotypes = biotypes;
    newBiotypes.sort((a, b) => b[NAME_BIOTYPE_PERCENT] - a[NAME_BIOTYPE_PERCENT]);

    return newBiotypes[0];
  }

  const calcPercentage = (percentage) => {
    if (percentage === QUANTITY_COUNT_INITIAL) return percentage;

    return ((percentage / biotypeQuestions.value.length) * 100).toFixed(2);
  }

  const setThreeHighestPercentages = () => {
    const biotypePercentage = biotypeCounts.value.map(element => ({
      biotype: element.biotype, 
      text: element.text, 
      percentage: calcPercentage(element.count), 
      video: element.video
    }));

    definedBiotype.value = getHighestPercent(biotypePercentage);
  }
</script>

<template>
  <Introduction 
    v-if="quizIntro" 
    @start="startQuiz"
  />

  <Quiz 
    v-else-if="!quizCompleted && !quizIntro"
    :isFirstQuestion="isFirstQuestion"
    :question="getCurrentQuestion"
    :totalQuestion="biotypeQuestions.length - 1"
    @previous="previousQuestion"
    @next="nextQuestion"
    @answer="setAnswer"
  />
  
  <QuizResult 
    v-else
    :biotype="definedBiotype"
  />
</template>
