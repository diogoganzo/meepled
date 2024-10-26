<template>
        <div class="image-wrapper">
          <VImg
            :src="image" 
            class="d-flex align-center justify-center"
            height="60vh" 
            cover
          >
          </VImg>
        </div>
  </template>
  
  <script setup>
  import { ref, onMounted, onUnmounted } from 'vue';

  const props = defineProps({
  image: {
    type: String,
    default: '/cover1.png'
  }
});
  </script>
  
  <style scoped>
  .image-wrapper {
    position: relative;
    overflow: hidden;
    height: 60vh; 
  }
  
  .image-wrapper::before {
    content: '';
    position: absolute;
    bottom: 0;
    left: 0;
    right: 0;
    height: 90%;
    background: linear-gradient(transparent, rgba(20, 24, 28, 1)); 
    z-index: 1;
  }
  
  .image-wrapper .v-img {
    position: relative;
    z-index: 0;
    width: 100%; 
    height: 100%; 
    object-fit: cover; 
  }
  </style>
  