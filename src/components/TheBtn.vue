<template>
  <button
    @click="clicked('stored')"
    :class="isSelected === 'stored' ? activeCss : deactiveCss"
  >
    Stored Resources
  </button>
  <button
    @click="clicked('add')"
    :class="isSelected === 'add' ? activeCss : deactiveCss"
  >
    Add Resources
  </button>
</template>
<script setup>
import { ref, computed } from "vue";

const isSelected = ref("stored");
const activeCss = [
  "bg-purple-900",
  "w-48",
  "text-white",
  "h-12",
  "font-semibold",
];
const deactiveCss = ["text-purple-900", "w-48", "h-12", "font-semibold"];

const clicked = (btn) => {
  isSelected.value = btn;
};
</script>
<style scoped></style>
