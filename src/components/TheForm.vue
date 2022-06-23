<template>
  <form @submit.prevent="updateData">
    <div class="max-w-3xl shadow-card mt-12">
      <div>
        <label
          for="title"
          class="block mb-2 text-sm font-medium text-gray-900 dark:text-gray-300"
          >Title</label
        >
        <input
          v-model="title"
          type="text"
          id="title"
          class="bg-gray-50 border border-gray-300 text-gray-900 text-sm rounded-lg focus:ring-blue-500 focus:border-blue-500 block w-full p-2.5 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500"
          placeholder="Title"
        />
      </div>
      <div>
        <label
          for="description"
          class="block mb-2 mt-4 text-sm font-medium text-gray-900 dark:text-gray-300"
          >Description</label
        >
        <input
          v-model="desc"
          type="text"
          id="description"
          class="bg-gray-50 border border-gray-300 text-gray-900 text-sm rounded-lg focus:ring-blue-500 focus:border-blue-500 block w-full p-2.5 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500"
          placeholder="Description"
        />
      </div>
      <div>
        <label
          for="link"
          class="block mb-2 mt-4 text-sm font-medium text-gray-900 dark:text-gray-300"
          >Link</label
        >
        <input
          v-model="link"
          type="text"
          id="link"
          class="bg-gray-50 border border-gray-300 text-gray-900 text-sm rounded-lg focus:ring-blue-500 focus:border-blue-500 block w-full p-2.5 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500"
          placeholder="https://www.google.com/"
        />
      </div>

      <button
        type="submit"
        class="text-white mt-8 bg-purple-700 hover:bg-purple-800 focus:ring-4 focus:outline-none focus:ring-blue-300 font-medium rounded-lg text-sm w-full sm:w-auto px-5 py-2.5 text-center dark:bg-blue-600 dark:hover:bg-blue-700 dark:focus:ring-blue-800"
      >
        Submit
      </button>
    </div>
  </form>
  <teleport to="body">
    <error-alert v-if="isInvalid">
      <template #head>
        <h2>Invalid Input</h2>
      </template>
      <template #desc>
        <p>
          Please check all inputs and make sure you enter at least a few
          characters into each input field.
        </p>
      </template>
      <template #actions>
        <button
          @click="invalidInput"
          class="w-20 bg-purple-900 text-white font-bold h-10 rounded"
        >
          Okay
        </button>
      </template>
    </error-alert>
  </teleport>
</template>

<script setup>
import ErrorAlert from "./ErrorAlert.vue";

import { reactive, ref } from "vue";
const title = ref(null);
const desc = ref(null);
const link = ref(null);
const isInvalid = ref(false);
const emit = defineEmits(["newdata"]);

const updateData = () => {
  if (!title.value || !desc.value || !link.value) {
    isInvalid.value = true;
  } else {
    const id = title.value.split(" ").join("-").toLowerCase();
    const newdata = {
      id,
      title: title.value,
      description: desc.value,
      link: link.value,
    };
    emit("newdata", newdata);
    title.value = null;
    desc.value = null;
    link.value = null;
  }
};
const invalidInput = () => {
  isInvalid.value = false;
};
</script>
