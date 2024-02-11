<script setup>
  const emit = defineEmits(['previous', 'next', 'answer']);

  defineProps({
    question: {
      question: String,
      options: {
        id: Number,
        biotype: String,
        option: String
      },
      selected: [null, Number]
    },
    isFirstQuestion: Boolean,
    totalQuestion: Number
  });

  const NAME_BUTTON_FINISH = 'Finalizar';
  const NAME_BUTTON_NEXT = 'Avançar';
  const NAME_BUTTON_SELECT_OPTION = 'Selecione uma opção';

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
  <section class="quiz">
    <div class="quiz-info">
      <span class="question">
        {{ question.question }}
      </span>
    </div>

    <div class="options">
      <label 
        v-for="(option, index) in question.options" 
        :key="option.id"
        :class="`option ${
          question.selected == index
            ? 'selected'
            : ''
        }`"
      >
        <input 
          type="radio" 
          :name="question.index"
          :value="index"
          @input="handleAnswerQuestion($event.target.value)"
        >

        <span>
          {{ option.option }}
        </span>
      </label>
    </div>

    <div class="wrapper-button">
      <button
        v-if="!isFirstQuestion"
        class="return-button"
        @click="handlePreviousQuestion"
      >
        Voltar
      </button>

      <button
        class="next-button"
        :disabled="question.selected === null"
        @click="handleNextQuestion"
      >
        {{ 
          question.index === totalQuestion
            ? NAME_BUTTON_FINISH
            : question.selected === null
              ? NAME_BUTTON_SELECT_OPTION
              : NAME_BUTTON_NEXT
        }}
      </button>
    </div>
  </section>
</template>

<style src="./index.css" scoped/>