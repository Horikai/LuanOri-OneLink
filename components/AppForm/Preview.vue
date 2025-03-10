<template>
  <div class="h-screen grid place-items-center">
    <div class="absolute top-4 right-4">
      <select id="iphone-model" v-model="selectedModel">
        <option value="iphone-12">iPhone 12</option>
        <option value="iphone-11">iPhone 11</option>
        <option value="iphone-x">iPhone X</option>
        <!-- Add more models as needed -->
      </select>
    </div>

    <DynamicIphoneFrame :model="selectedModel" backgroundImage="">
      <templates-simple :acc="data" />
    </DynamicIphoneFrame>

  </div>
</template>

<script setup>
import { ref } from 'vue';
import DynamicIphoneFrame from './DynamicIphoneFrame';

const props = defineProps({
  data: {
    type: Object,
    required: true,
  },
});

const selectedModel = ref('iphone-12'); // Default model, can be dynamically changed
</script>

<style scoped></style>
