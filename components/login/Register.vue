<template>
  <v-card class="text-center" height="100vh">
    <GeneralFadeImage :image="'/register.png'" />
    <v-fab class="mr-5" icon="mdi-close" location="top right" size="small" absolute @click="sheet = !sheet"
      style="z-index: 5" app></v-fab>
    <v-card-text>
      <div class="text-center w-50 text-white mx-auto position-relative"
        style="margin-top: -100px; position: relative; z-index: 3">
        <VImg src="/logo.png" width="150px" class="mx-auto align-center text-center justify-center" />
        <h2> Register </h2>
      </div>
      <v-text-field v-model="email" :rules="rules" label="Email Adress" hide-details></v-text-field>
      <v-text-field v-model="username" :rules="rules" label="Username" hide-details class="mt-2"></v-text-field>

      <v-text-field v-model="password" :rules="rules" class="mt-2" hide-details label="Password"></v-text-field>
      <v-checkbox v-model="checkbox" hide-details density="compact">
        <template v-slot:label>
          <div class="text-caption ml-2">
            I agree with the
            <v-tooltip location="bottom">
              <template v-slot:activator="{ props }">
                <a href="https://vuetifyjs.com" target="_blank" v-bind="props" @click.stop>
                  Terms of Use
                </a>
              </template>
              Opens in new window
            </v-tooltip>
          </div>
        </template>
      </v-checkbox>
      <v-checkbox v-model="checkbox" hide-details density="compact">
        <template v-slot:label>
          <div class="text-caption ml-2 text-center text-justify">
            I accept the
            <v-tooltip location="bottom">
              <template v-slot:activator="{ props }">
                <a href="https://vuetifyjs.com" target="_blank" v-bind="props" @click.stop>
                  Privacy Policy
                </a>
              </template>
              Opens in new window
            </v-tooltip>
            and consent to the procsseing of my personal information in accordance with it
          </div>
        </template>
      </v-checkbox>
      <v-row no-gutters>
        <v-col>
          <v-btn class="mt-2" type="submit" @click="emitChangePage('login')" block>Sign In</v-btn>
        </v-col>
        <v-col>
          <v-btn class="mt-2" type="submit" @click="emitChangePage('reset')" block>Reset Password</v-btn>
        </v-col>
        <v-col>
          <v-btn class="mt-2" type="submit" color='success' block>Join</v-btn>
        </v-col>
      </v-row>
    </v-card-text>
    <v-footer class="text-center pa-2" style="justify-content: center;">
      <span class="text-caption"> Artwork from <strong> Coimbra </strong> </span>
    </v-footer>
  </v-card>
</template>

<script setup>
import { ref, defineEmits } from "vue";
const emit = defineEmits(['changePage']);

const email = ref('');
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
