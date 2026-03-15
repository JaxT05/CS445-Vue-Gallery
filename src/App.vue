<script setup lang="ts">
import galleryData from './data.json'
import ImageThumbnail from './components/ImageThumbnail.vue';

const images = galleryData.galleryImages.sort(() => Math.random() - 0.5);
</script>

<template>
  <h1>Photo Gallery</h1>
  <h3>This is a collection of photos that I have taken while traveling over the past year or so.</h3>
  <h3> All were taken via my Coolpix camera, or my iPhone.</h3>
  <div class="image-grid">
    <div class="thumbnail-container" v-for="image in images" :key="image.name">
      <ImageThumbnail :imageUrl=image.url :imageCaption=image.name />
    </div>
  </div>
</template>
<style scoped>
.image-grid {
  display: flex;
  flex-wrap: wrap;
  width: 100%;
  .thumbnail-container {
    height: 20rem;
    flex-grow: 1;
    position: relative;
  }
}
</style>