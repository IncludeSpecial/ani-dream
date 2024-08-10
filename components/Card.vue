<script setup lang="ts">
const props = defineProps({
  post: {
    type: Object,
    required: true,
  },
});
</script>

<template>
  <div
      class=" p-4 bg-foreground gap-4 rounded-2xl flex flex-col shadow-lg transition-transform duration-500 hover:scale-105"
  >
    <NuxtImg
        :src="post?.image"
        :alt="post?.alt"

        class="w-full h-36 rounded-lg object-cover object-center transition-transform duration-700 "
    />


    <!-- Content Section -->
    <div class="flex-1 text-primary-foreground">
      <h3 class="text-lg font-bold  transition-colors duration-300 hover:text-yellow-400">{{ post.title }}</h3>
      <p class="text-sm  whitespace  text-gray-400">{{ post.description }}</p>
    </div>

    <!-- Meta Information -->
    <div class="">
      <div class="flex flex-wrap items-center  text-gray-500 ">
        <Icon name="mdi:label" class="text-lg mr-1"/>
        <template v-for="(category, index) in post.categories" :key="category">
          <span class="text-sm">{{ category }}<span v-if="index < post.categories.length - 1">&nbsp; </span> </span>
        </template>
      </div>
      <div class="text-sm text-gray-500 flex items-center">
        <Icon name="mdi:calendar-month-outline" class="text-lg mr-1"/>
        {{ post.date }}
      </div>
    </div>

    <NuxtLink
        :to="{name:'animes-anime', params:{anime: post.slug} }"
        class=" bg-yellow-500 text-gray-900 font-semibold text-center py-3 rounded-lg transition-all duration-300 hover:bg-yellow-600"
    >
      Смотреть
    </NuxtLink>
  </div>
</template>

<style scoped>

</style>
