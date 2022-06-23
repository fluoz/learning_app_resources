<template>
  <div class="h-24 mt-12 shadow-card flex items-center max-w-3xl">
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
  </div>
</template>
<script setup>
import { ref, computed } from "vue";
const props = defineProps({
  isSelected: {
    type: String,
    required: true,
  },
});
const activeCss = [
  "bg-purple-900",
  "w-48",
  "text-white",
  "h-12",
  "font-semibold",
];
const deactiveCss = ["text-purple-900", "w-48", "h-12", "font-semibold"];

const emit = defineEmits(["click-button"]);

const clicked = (btn) => {
  props.isSelected = btn;
  emit("click-button", btn);
};
</script>
<style scoped></style>
