<template>
  <div ref="me" class="greetings">
    <h1 class="green">{{ msg }}</h1>
    <h3>
      You’ve successfully created a project with
      <a href="https://vitejs.dev/" target="_blank" rel="noopener">Vite</a> +
      <a href="https://vuejs.org/" target="_blank" rel="noopener">Vue 3</a>.
    </h3>
  </div>
</template>

<script setup>
import { watch, ref } from "vue";
import { useElementVisibility } from "@vueuse/core";

defineProps({
  msg: {
    type: String,
    required: true,
  },
});

const me = ref(null);
const isVisible = useElementVisibility(me);
watch(isVisible, (newValue, oldValue) => {
  console.log(`visibilityUpdated NEW: ${newValue} OLD: ${oldValue}`);
});
</script>

<style scoped>
h1 {
  font-weight: 500;
  font-size: 2.6rem;
  top: -10px;
}

h3 {
  font-size: 1.2rem;
}

.greetings {
  background-color: red;
}
.greetings h1,
.greetings h3 {
  text-align: center;
}

@media (min-width: 1024px) {
  .greetings h1,
  .greetings h3 {
    text-align: left;
  }
}
</style>
