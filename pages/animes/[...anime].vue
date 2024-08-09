<script setup lang="ts">
import { onMounted, ref } from 'vue'
import { useRoute } from 'vue-router'
import { useHead } from '@vueuse/head'

const route = useRoute()
const anime = ref(null)

onMounted(async () => {
  const { anime: animeSlug } = route.params

  // Fetch the anime content using the slug from the URL
  const fetchedAnime = await queryContent('animes').where({ slug: animeSlug[0] }).findOne()
  anime.value = fetchedAnime

  // Log the fetched anime object
  console.log('Fetched anime object:', fetchedAnime)

  // Set the page's meta tags and title based on the fetched anime data
  useHead({
    title: fetchedAnime?.title || 'Аниме',
    meta: [
      {
        name: 'description',
        content: fetchedAnime?.description || 'Описание аниме',
      },
    ],
  })
})
</script>

<template>
  <div>
    <article v-if="anime" class="bg-foreground text-primary-foreground rounded-lg shadow-lg p-8 mx-auto">
      <h1 class="text-4xl font-bold mb-4 border-b-2 border-yellow-500 pb-2">{{ anime.title }}</h1>
      <div class="flex flex-row gap-4 items-center">
        <NuxtImg :src="anime.image" :alt="anime.title" class="w-96 object-cover rounded-lg shadow-md" />
        <p class="mb-4 text-lg">{{ anime.descriptionFull }}</p>
      </div>
      <p class="mb-4"><strong>Категории:</strong> {{ anime.categories.join(', ') }}</p>
      <p class="mb-4"><strong>Дата выхода:</strong> {{ anime.date }}</p>
      <div v-if="anime.body?.toc">
        <p v-for="(link, index) in anime.body.toc.links" :key="index">{{ link.text }}</p>
      </div>
    </article>
    <p v-else class="text-8xl text-center">
      <Icon name="tabler:loader" class="animate-spin" />
      Загрузка...
    </p>
  </div>
</template>
