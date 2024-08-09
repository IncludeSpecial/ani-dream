<script setup lang="ts">
import { useRoute } from 'vue-router';
import Card from '~/components/Card.vue';

const route = useRoute();
const { data } = await useAsyncData('category-animes', () =>
    queryContent('/animes')
        .where({ categories: { $contains: route.params.category } })
        .find()
);

useHead({
  title: `Категории | Ani-Dream`,
  meta: [
    {
      name: "description",
      content: `Аниме в категории: ${route.params.category}`
    }
  ]
});
</script>

<template>
  <section>
    <h1 class="text-3xl font-bold mb-6">Аниме в категории: {{ route.params.category }}</h1>
    <div class="grid grid-cols-4 gap-4">
      <Card
          v-for="anime in data"
          :key="anime._path"
          :post="anime"
      />
    </div>
  </section>
</template>
