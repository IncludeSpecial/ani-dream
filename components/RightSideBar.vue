<!--components/RightSideBar.vue-->
<template>
  <aside class="w-72 flex flex-col p-4 bg-foreground text-primary-foreground dark:text-primary-foreground dark:bg-foreground border-b-4 border-red-500">
    <!-- Просмотренные аниме Section -->
    <div class="mb-4 pb-4 border-b-4 border-red-500">
      <div class="font-bold flex whitespace-nowrap items-center gap-2">
        <Icon name="mdi:menu" size="16px"/>
        Просмотренные аниме
      </div>
    </div>

    <!-- Избранные аниме Section -->
    <div class="mb-4 pb-4 border-b-4 border-red-500">
      <div class="font-bold flex whitespace-nowrap items-center gap-2">
        <Icon name="mdi:menu" size="16px"/>
        Избранные аниме
      </div>
    </div>

    <!-- Последние обновления Section -->
    <div>
      <div class="font-bold flex whitespace-nowrap items-center gap-2 mb-4 pb-4 border-b-4 border-red-500">
        <Icon name="mdi:menu" size="16px"/>
        Последние обновления
      </div>
      <div class="flex gap-4 flex-col">
        <div class="flex flex-col items-start gap-4">
          <img src="https://staticg.sportskeeda.com/editor/2023/12/54e67-17019438061017-1920.jpg" alt="Update Image" class="object-cover rounded-lg"/>
          <div class="flex flex-col space-y-2">
            <div class="text-primary-foreground font-semibold whitespace-nowrap">Длинное название аниме</div>
            <div class="text-muted-foreground text-sm">Сегодня 20:00</div>
            <div class="text-muted-foreground text-sm">12 серий</div>
          </div>
        </div>
      </div>
    </div>
  </aside>
</template>
