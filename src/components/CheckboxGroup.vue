<template>
  <div class="checkboxes-container">
    <div class="checkbox-group">
      <div class="checkbox-button" v-for="option in options" :key="option.id">
        <button
          type="button"
          :class="{ 'active': selectedOption === option.id }"
          @click="selectOption(option.id)"
        >
          {{ option.text }}
        </button>
      </div>
      <button class="check-button" @click="checkButtonClicked">Check</button>
    </div>
  </div>
</template>

<script setup>
import { defineProps, defineEmits } from 'vue';

const props = defineProps({
  options: {
    type: Array,
    required: true,
  },
  selectedOption: {
    type: Number,
    required: true,
  },
});

const emit = defineEmits(['select', 'check']);

const selectOption = (optionId) => {
  emit('select', optionId);
};

const checkButtonClicked = () => {
  emit('check', props.selectedOption);
};
</script>

<style scoped>
.checkboxes-container {
  display: grid;
  grid-template-columns: repeat(1, 1fr);
  gap: 10px;
  margin-top: 20px;
}

.checkbox-group {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  gap: 10px;
}

.checkbox-button,
.check-button {
  grid-column: span 1;
}

.checkbox-button button,
.check-button button {
  width: 100%;
  padding: 10px 20px;
  border: 1px solid #ccc;
  cursor: pointer;
}

 .active {
  background-color: #007bff;
  color: #fff;
}

@media (max-width: 768px) {


  .checkboxes-container {
    grid-template-columns: 1fr;

  }

  .checkbox-group {
    padding: 10px;
  }

  .checkbox-button button, 
  .check-button {
    padding: 5px;
  }


}
</style>