<!--components/LeftSideBarItem-->
<template>
  <a :href="link" class="hover:text-foreground dark:hover:text-foreground">
    {{ name }}
  </a>
</template>

<script setup lang="ts">
const props = defineProps<{
  name: string;
  link: string;
}>();
</script>

<style scoped>
a {
  color: #a0aec0; /* Gray-500 */
  transition: color 0.3s;
}
</style>
