<template>
  <a :href="link" class="block">
    <NuxtImg :src="image" alt="Collection Image" class="w-full h-auto rounded-lg mb-2" />
    <div class="text-center font-semibold">{{ name }}</div>
  </a>
</template>

<script setup lang="ts">
defineProps<{
  name: string;
  image: string;
  link: string;
}>();
</script>
