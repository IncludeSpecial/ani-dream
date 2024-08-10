
<script setup lang="ts">

const { data } = await useAsyncData('categories-list', () =>
    queryContent('/animes')
        .only(['categories'])
        .find()
);

const categories = computed(() => {
  const catSet = new Set();
  data.value.forEach((anime) => {
    anime.categories.forEach((category) => {
      catSet.add(category);
    });
  });
  return Array.from(catSet);
});
</script>

<template>
  <div>
    <h1 class="text-3xl font-bold mb-6">Страница категорий</h1>
    <ul>
      <li v-for="category in categories" :key="category">
        <NuxtLink :to="`/categories/${category}`">{{ category }}</NuxtLink>
      </li>
    </ul>
  </div>

</template>
