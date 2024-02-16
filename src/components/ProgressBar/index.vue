<script setup>
  defineProps({
    progress: Number,
  });
</script>

<template>
  <div class="progress-bar">
    <div 
      class="progress-bar__inner" 
      :style="{ width: `${progress}%` }"
      :data-progress="`${progress}%`"
    ></div>
  </div>
</template>

<style src="./index.css" scoped/>