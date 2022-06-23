<template>
  <the-header></the-header>
  <div class="max-w-3xl mx-auto">
    <the-btn @ClickButton="getButton"></the-btn>
    <ul v-if="isSelected === 'stored'">
      <the-resource
        v-for="resource in storedResources"
        :data="resource"
        :key="resource.id"
        @deleteid="emitId"
        @click="deleteResource(delId)"
      ></the-resource>
    </ul>
  </div>
</template>

<script setup>
import { ref } from "vue";
import TheHeader from "./components/TheHeader.vue";
import TheBtn from "./components/TheBtn.vue";
import TheResource from "./components/TheResource.vue";

const isSelected = ref("stored");
const delId = ref("null");

const emitId = (value) => {
  delId.value = value;
};
const storedResources = ref([
  {
    id: "official-guide",
    title: "Official Guide",
    description: "The official Vue.js documentation.",
    link: "https://vuejs.org/",
  },
  {
    id: "google-guide",
    title: "Google Guide",
    description: "The official Google documentation.",
    link: "https://google.com/",
  },
]);

const getButton = (value) => {
  isSelected.value = value;
};

const deleteResource = (id) => {
  storedResources.value = storedResources.value.filter(
    (resource) => resource.id !== id
  );
};
</script>
<style>
.shadow-card {
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.26);
  max-width: 40rem;
  padding: 1rem;
  border-radius: 12px;
}

html {
  font-family: sans-serif;
}
</style>
