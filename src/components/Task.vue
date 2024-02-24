<template>
  <div class="middle-section">
    <h1>{{ task.title }}</h1>
    <h2>{{ task.subtitle }}</h2>
    <img :src="task.image" alt="Image" class="image">
    <CheckboxGroup :options="task.options" :selectedOption="selectedOption" @select="selectOption" @check="checkButtonClicked" />
  </div>
</template>

<script setup>
import { ref, defineProps } from 'vue';
import CheckboxGroup from '@/components/CheckboxGroup.vue';

const props = defineProps({
  task: {
    type: Object,
    required: true,
  },
});

const selectedOption = ref(null);

const selectOption = (optionId) => {
  selectedOption.value = optionId;
};

const checkButtonClicked = (selectedOptionId) => {
  if (selectedOptionId === props.task.correctAnswer) {
    alert('Верно!');
  } else {
    alert('Неверно! Попробуйте снова.');
  } 
  selectedOption.value = null; 
};
</script>

<style scoped>
.middle-section {
  display: grid;
  place-items: center;
  text-align: center;
  gap: 50px;
}

.image {
  max-width: 100%;
  height: auto;
}

.check-button {
  grid-column: span 1;
  padding: 10px;
}
</style>