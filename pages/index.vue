<template>
  <VContainer fluid class="h-100 pa-0" style="max-height: 100vh;">
    <VCol class="pa-0 m-0">
      <div class="image-wrapper">
        <VImg
          :src="currentImage" 
          class="d-flex align-center justify-center"
          height="400" 
          cover
        >
        </VImg>
      </div>
    </VCol>
    <div class="text-center w-50 text-white mx-auto position-relative" style="margin-top: -101px; position: relative; z-index: 3;">
      <img src="/logo-with-name.png" width="150px" class="mx-auto align-center text-center justify-center">
    </div>
    <VCol cols="12" md="12" lg="12" sm="12">
      <VRow no-gutters align="center" justify="center">
        <VCol cols="12" md="6">
          <v-list :items="items" bg-color="background"></v-list>
        </VCol>
      </VRow>
    </VCol>
  </VContainer>
</template>

<script setup>
import { ref, onMounted, onUnmounted } from 'vue';

const images = [
  '/cover1.png',
  '/cover2.png',
  '/cover3.png',
];

const items = [
        {
          title: 'Sign in',
          value: 1,
        },
        { type: 'divider' },
        {
          title: 'Create account',
          value: 2,
        },
        { type: 'divider' },
        {
          title: 'Open the tour',
          value: 3,
        },
      ];

const currentIndex = ref(0);
const currentImage = ref(images[currentIndex.value]);

const changeImage = () => {
  currentIndex.value = (currentIndex.value + 1) % images.length;
  currentImage.value = images[currentIndex.value];
};

let imageInterval;

onMounted(() => {
  imageInterval = setInterval(changeImage, 10000); // Trocar a imagem a cada 5 segundos
});

onUnmounted(() => {
  clearInterval(imageInterval); // Limpar o intervalo ao desmontar o componente
});
</script>

<style scoped>
.image-wrapper {
  position: relative;
  overflow: hidden;
  height: 400px; /* Defina a altura fixa desejada */
}

.image-wrapper::before {
  content: '';
  position: absolute;
  bottom: 0;
  left: 0;
  right: 0;
  height: 90%;
  background: linear-gradient(transparent, rgba(20, 24, 28, 1)); /* Gradiente de transparente para #14181c */
  z-index: 1;
}

.image-wrapper .v-img {
  position: relative;
  z-index: 0;
  width: 100%; /* Garante que a imagem ocupe toda a largura do contêiner */
  height: 100%; /* Garante que a imagem ocupe toda a altura do contêiner */
  object-fit: cover; /* Ajusta a imagem para cobrir o contêiner sem distorção */
}
</style>
