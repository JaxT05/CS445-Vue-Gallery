<script setup lang="ts">
import { ref } from 'vue';
import ImageModal from './ImageModal.vue';

const showModal = ref(false);
</script>
<template>
    <img :src="imageUrl" loading="lazy">
    <ImageModal :showModal="showModal" :imageUrl="imageUrl" @close="showModal = false" />
    <div @click="showModal = true" class="mouse-over-container"><p>{{ imageCaption }}</p></div>

</template>
<script lang="ts">
    export default {
    name: 'ImageThumbnail',
    props: {
        imageUrl: {
        type: String,
        required: true
        },
        imageCaption: {
        type: String,
        required: true
        }
    }
    };
</script>
<style scoped>
img {
    max-height: 100%;
    min-width: 100%;
    object-fit: cover;
    vertical-align: bottom;
}
.mouse-over-container {
      opacity: 0;
      position: absolute;
      top: 0;
      bottom: 0;
      left: 0;
      right: 0;
      height: 100%;
      transition: .5s ease;
      background-color: #00000080;
      color: white;
      p {
        position: absolute;
        top: 50%;
        left: 50%;
        transform: translate(-50%, -50%);
      }
    }
    .mouse-over-container:hover {
        opacity: 1;
    }
</style>