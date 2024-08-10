<!--components/LeftSideBar.vue-->
<script setup lang="ts">
import { ref } from 'vue';

import { useAsyncData } from '#app';

// Define the type for your content data (categories)
interface AnimeContent {
  categories: string[];
}

// Fetch genres dynamically from the content
const genres = ref<string[]>([]);

const { data } = await useAsyncData<AnimeContent[]>('genres', () =>
    queryContent('/animes')
        .only(['categories', "categoriesSlug"])
        .find()
);

if (data.value) {
  const genresMap = new Map<string, string>();
  data.value.forEach((anime) => {
    anime.categories.forEach((category, index) => {
      const slug = anime.categoriesSlug[index];
      if (!genresMap.has(category)) {
        genresMap.set(category, slug);
      }
    });
  });
  genres.value = Array.from(genresMap).map(([name, slug]) => ({ name, slug }));
}
</script>

<template>
  <aside class="flex flex-col w-72 top-0 sticky p-4 h-full bg-foreground text-primary-foreground border-b-4 border-red-500 pb-4">
    <!-- Genres Section -->
    <div class="flex-col flex">
      <NuxtLink to="/categories" class="font-bold items-center gap-2 mb-4">
        <Icon name="mdi:menu" size="16px"/>
        Жанры
      </NuxtLink>
      <div>
        <div class="flex-wrap flex justify-between gap-4 text-sm border-b-4 border-red-500 pb-4">
          <LeftSideBarItem
              v-for="genre in genres"
              :key="genre.slug"
              :name="genre.name"
              :link="`/categories/${genre.slug}`"/>
        </div>
      </div>
    </div>

    <!-- Collections Section -->
    <div class="collections">
      <div class="font-bold flex items-center gap-2 mb-4">
        <Icon name="mdi:collections-bookmark" size="16px"/>
        Подборки
      </div>
      <div class="collection-items space-y-4">
        <CollectionItem name="Школа"
                        image="https://staticg.sportskeeda.com/editor/2023/12/54e67-17019438061017-1920.jpg?w=640"
                        link="#"/>
        <CollectionItem name="Магия"
                        image="https://honeysanime.com/wp-content/uploads/2017/07/Rokudenashi-Majutsu-Koushi-to-Akashic-Records-Wallpaper.jpg"
                        link="#"/>
        <CollectionItem name="Любовь"
                        image="https://as2.ftcdn.net/v2/jpg/05/56/62/65/1000_F_556626587_NYmwKW2MRnrLQn6jSybCYhR6rdwcWIXl.jpg"
                        link="#"/>
        <CollectionItem name="Демоны"
                        image="https://static1.moviewebimages.com/wordpress/wp-content/uploads/2023/10/the-15-best-anime-series-about-demons.jpg"
                        link="#"/>
      </div>
    </div>
  </aside>
</template>
