<template>
    <VContainer fluid class="h-95 pa-0" style="max-height: calc(100vh - 80px)">
        <div class="text-center w-30  mt-2 text-white mx-auto position-relative">
      <img src="/logo-text.png" width="100px" class="mx-auto align-center text-center justify-center" />
    </div>
        <v-tabs v-model="tab" align-tabs="center">
            <v-tab :value="1">Boardgames</v-tab>
            <v-tab :value="2">Reviews</v-tab>
            <v-tab :value="3">Lists</v-tab>
        </v-tabs>

        <v-tabs-window v-model="tab">
            <v-tabs-window-item v-for="n in 3" :key="n" :value="n">
                <v-container fluid>
                    <v-row>
                        <v-col v-for="i in 6" :key="i" cols="12" md="4">
                            <v-img :lazy-src="`https://picsum.photos/10/6?image=${i * n * 5 + 10}`"
                                :src="`https://picsum.photos/500/300?image=${i * n * 5 + 10}`" height="205"
                                cover></v-img>
                        </v-col>
                    </v-row>
                </v-container>
            </v-tabs-window-item>
        </v-tabs-window>
    </VContainer>
</template>

<script setup>
import { ref, onMounted, onUnmounted } from "vue";

const tab = ref(null);
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