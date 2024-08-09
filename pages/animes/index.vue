<!--pages/animes/index.vue-->
<script setup lang="ts">


import Card from "~/components/Card.vue";

const  data  = await queryContent('/animes')
    .only(['_path', 'title', 'slug' , 'description', 'date', 'categories', 'image'])
    .sort({ date: -1 })
    .find()



useHead({
  title: "Аниме | Ani-Dream",
  meta: [
    {
      name: "description",
      content: 'My amazing site.'
    }
  ]
});
</script>

<template>
  <div class="flex-col flex ">

    <h1 class="text-3xl font-bold mb-6">Аниме страница</h1>
    <section class="grid grid-cols-4 gap-4 ">
      <Card
          v-for="anime in data"
          :key="anime._path"
          :post="anime"
      />

  </section>
  </div>
</template>
