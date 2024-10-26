<template>
  <VContainer fluid class="h-95 pa-0" style="max-height: calc(100vh - 56px)">
    <VCol class="pa-0 m-0">
      <GeneralFadeImage :image="currentImage.src" />
    </VCol>
    <div class="text-center w-50 text-white mx-auto position-relative"
      style="margin-top: -100px; position: relative; z-index: 3">
      <img src="/logo-with-name.png" width="150px" class="mx-auto align-center text-center justify-center" />
    </div>
    <VCol cols="12" md="12" lg="12" sm="12">
      <VRow no-gutters align="center" justify="center">
        <VCol cols="12" md="6">
          <v-list>
            <template v-for="item in items" :key="item.value">
              <v-list-item v-if="item.title" @click="onListClick(item)" class="my-list-item">
                <v-list-item-title>{{ item.title }}</v-list-item-title>
              </v-list-item>
              <v-divider v-else-if="item.type === 'divider'" />
            </template>
          </v-list>
        </VCol>
      </VRow>
    </VCol>
    <v-bottom-sheet v-model="sheet" class="mt-0" fullscreen>
      <Login  @changePage="handlePageChange" v-show="selectedItem == 1"></Login>
      <LoginRegister @changePage="handlePageChange" v-show="selectedItem == 2"></LoginRegister>
      <LoginResetPassword @changePage="handlePageChange" v-show="selectedItem == 4"></LoginResetPassword>
      <v-fab class="mr-5" icon="mdi-close" location="top right" size="small" absolute @click="sheet = !sheet"
          style="z-index: 5" app></v-fab>
    </v-bottom-sheet>
    <v-footer class="text-center pa-2" style="justify-content: center; bottom: 15px;">
      <span class="text-caption">Artwork from <strong>{{ currentImage.author }} </strong> </span>
    </v-footer>
  </VContainer>
</template>

<script setup>
import { ref, onMounted, onUnmounted } from "vue";

const images = [
  { src: "/cover1.png", author: "Above and Bellow" },
  { src: "/cover2.png", author: "High Society" },
  { src: "/cover3.png", author: "Wingspan" }
];

const items = [
  { title: "Sign in", value: 1 },
  { type: "divider" },
  { title: "Create account", value: 2 },
  { type: "divider" },
  { title: "Open the tour", value: 3 },
];

const currentIndex = ref(0);
const selectedItem = ref(1);
const currentImage = ref(images[currentIndex.value]);
const sheet = ref(false);

const changeImage = () => {
  currentIndex.value = (currentIndex.value + 1) % images.length;
  currentImage.value = images[currentIndex.value];
};

let imageInterval;

const onListClick = (item) => {
  selectedItem.value = item.value;
  sheet.value = true;
};
function handlePageChange(option) {
  if (option === 'join') selectedItem.value = 2;
  else if (option === 'login') selectedItem.value = 1;
  else if (option === 'reset') selectedItem.value = 4;
}

onMounted(() => {
  imageInterval = setInterval(changeImage, 10000);
});

onUnmounted(() => {
  clearInterval(imageInterval);
});
</script>

<style scoped>
.image-wrapper {
  position: relative;
  overflow: hidden;
  height: 60vh;
}
.image-wrapper::before {
  content: "";
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
