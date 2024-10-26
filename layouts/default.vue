<template>
  <div>
    <VApp>
      <VMain>
        <slot />
        <v-bottom-navigation density="compact" bg-color="#445565">
          <v-btn value="recent">
            <v-icon>mdi-account-lock</v-icon>
          </v-btn>

          <v-btn value="home" :to="'/home'">
            <v-icon>mdi-card-multiple</v-icon>
          </v-btn>

          <v-btn value="nearby">
            <v-icon>mdi-magnify</v-icon>
          </v-btn>
        </v-bottom-navigation>
      </VMain>
    </VApp>
  </div>
</template>
