<!-- Modal.vue -->
<template>
  <div v-if="isOpen" class="modal-overlay">
    <div class="modal">
      <button class="close-button" @click="$emit('close')">
        <img src="@/assets/close_btn.png" alt="Close">
      </button>
      <slot></slot>
    </div>
  </div>
</template>
  
<script>
export default {
  props: {
    isOpen: {
      type: Boolean,
      default: false
    }
  }
}
</script>
  
<style scoped>
.modal-overlay {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, 0.5);
  display: flex;
  justify-content: center;
  align-items: center;
  z-index: 9999;
}

.modal {
  background-color: #fff;
  padding: 20px;
  border-radius: 5px;
  position: relative;
}

.close-button {
  position: absolute;
  top: 10px;
  right: 10px;
  width: 20px;
  height: 20px;
  background: none;
  border: none;
  cursor: pointer;
  padding: 0;
}

.close-button img {
  width: 100%;
  height: 100%;
}
</style>