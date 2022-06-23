<template>
  <li class="list-none max-w-3xl shadow-card mt-8 flex justify-between">
    <div>
      <h2 class="font-bold text-2xl">{{ data.title }}</h2>
      <p class="mt-4 font-medium">{{ data.description }}</p>
      <a
        target="blank"
        class="font-semibold text-yellow-600 mt-2"
        :href="data.link"
        >View Resource</a
      >
    </div>
    <div>
      <button
        @click="emit('deleteid', data.id)"
        class="text-purple-900 font-semibold w-20 h-8 hover:bg-purple-200"
      >
        Delete
      </button>
    </div>
  </li>
</template>

<script setup>
const props = defineProps({
  data: {
    type: Object,
    required: true,
  },
});
const emit = defineEmits(["deleteid"]);
</script>
