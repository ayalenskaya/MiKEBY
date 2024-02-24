<template>
  <div class="page-container">
    <!-- <div class="left-section">
      <br>
      <button class="close-button"></button>
    </div>

  отправила этот close-button в модалку 
      -->

    <Task :task="task" />
    <div class="right-section">

      <div class="action"> Anton <br>
        1000 <img src="@/assets/coin.png" alt="Action Icon" class="action-icon"></div>
      <button class="bulb-button" @click="isModalOpen = true">
      </button>


      <Modal :is-open="isModalOpen" @close="isModalOpen = false">

        <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Ab a animi corrupti quis similique ipsam provident
          doloribus quas accusantium, repellendus atque nisi ducimus blanditiis, optio commodi quibusdam veniam ullam
          libero?</p>
      </Modal>
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue';
import task from '@/assets/task.json';
import Task from '@/components/Task.vue';
import Modal from '@/components/Modal.vue';

const isModalOpen = ref(false); 
</script>

<style scoped>
.page-container {
  display: grid;
  grid-template-columns: auto 1fr auto;
  gap: 20px;
}

.middle-section {
  grid-column: 2 / span 1;
  /* Указываем, что middle-section должен занимать вторую колонку */
}

.right-section {
  grid-column: 3 / span 1;
  /* Указываем, что right-section должен занимать третью колонку */
  display: grid;
  grid-template-rows: repeat(2, 1fr);
  align-items: start;
}

.close-button,
.bulb-button {
  width: 20px;
  background-repeat: no-repeat;
  background-position: center;
  background-size: contain;
  cursor: pointer;
  background-image: url('@/assets/bulb.png');
}




@media (max-width: 768px) {

  .page-container {
    grid-template-columns: 1fr;
  }

  .middle-section,
  .right-section {
    grid-column: 1 / span 1;
    text-align: center;
    justify-content: center;
  }

  .action {
    text-align: start;
    margin-bottom: 15px;
  }
}
</style>