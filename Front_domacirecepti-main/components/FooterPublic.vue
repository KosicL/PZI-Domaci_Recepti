<script setup lang="ts">
import {ref} from 'vue'

const icons = ref( [
  'mdi-facebook',
  'mdi-twitter',
  'mdi-linkedin',
  'mdi-instagram',
])
</script>

<template>
  <v-footer class="footer"
      color="#C87C36"
  >
    <div style="position: absolute; display: flex">
      <v-btn
          v-for="icon in icons"
          :key="icon"
          class="mx-4 "
          :icon="icon"
          variant="text"
      ></v-btn>
    </div>

    <v-spacer></v-spacer>

    <div>
      {{ new Date().getFullYear() }} — <strong>Vuetify</strong>
    </div>
  </v-footer>
</template>

<style scoped>

.footer{
  display: flex;
  justify-content: center;
  align-items: center;
  padding: 20px;
}

</style>