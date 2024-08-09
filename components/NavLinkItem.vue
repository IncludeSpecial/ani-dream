
<template>
  <nuxt-link :to="link" class="p-2 flex flex-row bg-secondary-foreground text-secondary rounded gap-2 items-center">
    <Icon :name="icon" :size="size" />
    {{ name }}
  </nuxt-link>
</template>

<script setup lang="ts">

defineProps<{
  name: string;
  link: string;
  icon?: string;
  size?: string;
}>();

</script>
