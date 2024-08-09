<template>

  <NavigationBar/>
  <div class="flex flex-col min-h-screen">
    <!-- Header -->


    <!-- Main Content Area -->
    <div class="flex flex-1 gap-4">
      <!-- Left Aside -->
      <LeftSideBar/>
      <!-- Main Content -->
      <main class="flex flex-col ">
        <slot/>
      </main>
      <RightSideBar/>

    </div>

    <!-- Footer -->
    <footer class=" text-white p-4">
      <div class="container mx-auto text-center">
        &copy; 2024 Your Company. All rights reserved.
      </div>
    </footer>
  </div>
</template>
<script setup lang="ts">
</script>