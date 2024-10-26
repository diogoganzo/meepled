<template>
      <v-card class="text-center" height="100vh">
        <GeneralFadeImage :image="'/login.png'" />
        <v-card-text>
          <div class="text-center w-50 text-white mx-auto position-relative"
            style="margin-top: -100px; position: relative; z-index: 3">
            <VImg src="/logo.png" width="150px" class="mx-auto align-center text-center justify-center" />
            <h2> Login </h2>
          </div>
          <br />
          <br />

          <v-text-field
        v-model="username"
        :rules="rules"
        label="Username"
      ></v-text-field>

      <v-text-field
        v-model="password"
        :rules="rules"
        label="Password"
      ></v-text-field>
        <v-row> 
          <v-col>
      <v-btn class="mt-2" type="submit" @click="emitChangePage('join')" block>Join</v-btn>
    </v-col>
    <v-col>
      <v-btn class="mt-2" type="submit" @click="emitChangePage('reset')" block>Reset Password</v-btn>
    </v-col>
    <v-col>
      <v-btn class="mt-2" type="submit" color='success' block>Login</v-btn>
    </v-col>
        </v-row>
        </v-card-text>
        <v-footer class="text-center pa-2" style="justify-content: center;">
      <span class="text-caption"> Artwork from <strong> When I Dream </strong> </span>
    </v-footer>
      </v-card>
</template>

<script setup>

import { ref, defineEmits } from "vue";

const emit = defineEmits(['changePage']);

const username = ref('');
const password = ref('');
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

