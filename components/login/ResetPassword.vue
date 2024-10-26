<template>
    <v-card class="text-center" height="100vh">
      <GeneralFadeImage :image="'/forgotPassword.png'" />
      <v-card-text>
        <div class="text-center w-100 text-white mx-auto position-relative"
          style="margin-top: -100px; position: relative; z-index: 3">
          <VImg src="/logo.png" width="150px" class="mx-auto align-center text-center justify-center" />
          <h2> Reset Password </h2>
        </div>
        <br />
        <br />

        <v-text-field
      v-model="email"
      :rules="rules"
      label="Email Adress"
    ></v-text-field>

      <v-row> 
        <v-col>
    <v-btn class="mt-2" type="submit" @click="emitChangePage('login')" block>Sign In</v-btn>
  </v-col>
  <v-col>
    <v-btn class="mt-2" type="submit" @click="emitChangePage('join')" block>Join</v-btn>
  </v-col>
  <v-col>
    <v-btn class="mt-2" type="submit" color='success' block>Reset</v-btn>
  </v-col>
      </v-row>
      </v-card-text>
      <v-footer class="text-center pa-2" style="justify-content: center;">
      <span class="text-caption"> Artwork from <strong> Human Era </strong> </span>
    </v-footer>
    </v-card>
</template>

<script setup>

import { ref, defineEmits } from "vue";

const emit = defineEmits(['changePage']);

const email = ref('');
const rules = ref([
      value => {
        if (value) return true

        return 'Field is required'
      },
    ],)

function emitChangePage(option) {
emit('changePage', option); 
}
</script>

