<script setup>
  import { computed } from 'vue'

  import ProgressBar from '../ProgressBar/index.vue';
  
  const emit = defineEmits(['previous', 'next', 'answer']);

  const props = defineProps({
    question: {
      question: String,
      options: {
        id: Number,
        biotype: String,
        option: String
      },
      selected: [null, Number],
      index: Number
    },
    isFirstQuestion: Boolean,
    totalQuestion: Number,
    positionQuestion: Number,
  });

  const NAME_BUTTON_FINISH = 'Finalizar';
  const NAME_BUTTON_NEXT = 'Avançar';
  const NAME_BUTTON_SELECT_OPTION = 'Selecione uma opção';
  const ONE_HUNDRED = 100;

  const progress = computed(() => {
    return ((props.positionQuestion * ONE_HUNDRED) / props.totalQuestion).toFixed(0);
  })

  const handlePreviousQuestion = () => {
    emit('previous');
  }

  const handleNextQuestion = () => {
    emit('next');
  }

  const handleAnswerQuestion = (indexQuestion) => {
    emit('answer', Number(indexQuestion));
  }
</script>

<template>
  <section class="section__quiz">
    <ProgressBar 
      :progress="progress"
    />
  
    <div class="container-quiz">
      <div class="quiz__question">
        <span class="question__title">
          {{ question.question }}
        </span>
      </div>
  
      <div class="quiz__options">
        <label 
          v-for="(option, index) in question.options" 
          :key="`${option.id}-${option.option}`"
          :class="`quiz__option ${
            question.selected === index
              ? '--selected'
              : ''
          }`"
        >
          <input 
            type="radio"
            :name="question.index"
            :value="option.id"
            class="quiz__input"
            @input="handleAnswerQuestion($event.target.value)"
          >
  
          <span class="option__title">
            {{ option.option }}
          </span>
        </label>

        <span 
          v-if="question.selected === null"
          class="quiz__selection-option"
        >
          {{ NAME_BUTTON_SELECT_OPTION }}
        </span>
      </div>
  
      <div class="quiz__wrapper-button">
        <button
          v-if="!isFirstQuestion"
          class="button__previous"
          @click="handlePreviousQuestion"
        >
          Voltar
        </button>
  
        <button
          class="button__next"
          :disabled="question.selected === null"
          @click="handleNextQuestion"
        >
          {{ 
            question.index === totalQuestion
              ? NAME_BUTTON_FINISH
              : NAME_BUTTON_NEXT
          }}
        </button>
      </div>
    </div>
  </section>
</template>

<style src="./index.css" scoped/>