<script setup lang="ts">
import { onMounted, ref, provide } from "vue";

const msg = ref<string>("Vite + Vue--------APP");
provide("app-msg", msg.value);
const show = ref<boolean>(true);
const propsRef = ref<HTMLElement | null>(null);
const watchRef = ref<HTMLElement | null>(null);
onMounted(() => {
  console.log("------------>propsRef", propsRef.value);
  console.log("-------------->watchRef", watchRef.value);
});
</script>

<template>
  <router-view></router-view>
</template>

<style scoped>
.logo {
  height: 6em;
  padding: 1.5em;
  will-change: filter;
  transition: filter 300ms;
}
.logo:hover {
  filter: drop-shadow(0 0 2em #646cffaa);
}
.logo.vue:hover {
  filter: drop-shadow(0 0 2em #42b883aa);
}
</style>
