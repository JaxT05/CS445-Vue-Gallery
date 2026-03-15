<script setup lang="ts">
defineProps(["showModal", "imageUrl"]);
const modalStates = defineEmits(["close"]);
const closeModal = () => modalStates("close");
</script>

<template>
  <div v-if="showModal" class="modal-backdrop" @click.self="closeModal">
    <div class="modal">
      <button class="close-button" @click="closeModal">×</button>
      <img class="modal-image":src="imageUrl" />
    </div>
  </div>
</template>

<style scoped>
.modal {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    display: flex;
    justify-content: center;
    align-items: center;
    background-color: rgba(15, 15, 15, 0.9);
    z-index: 1000;
}
.modal-image{ 
    max-height: 80%;
    box-shadow: 0 0 30px 0px rgba(255, 255, 255, 0.1);
}
.close-button {
    position: absolute;
    padding: 1rem;
    top: 10px;
    right: 10px;
    background: none;
    border: none;
    font-size: 2rem;
    cursor: pointer;
}
</style>