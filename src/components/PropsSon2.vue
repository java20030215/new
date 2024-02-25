<template>
    <h1>{{ title }}</h1>
</template>
<script setup lang="ts">
import { defineProps } from 'vue';
const props = defineProps<{ title: string }>();
</script>
