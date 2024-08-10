<template>

  <NavigationBar/>
  <div class="">
    <!-- Header -->


    <!-- Main Content Area -->
    <div class="flex flex-1 gap-4">
      <!-- Left Aside -->
      <left-side-bar class="lg:flex hidden"/>
      <!-- Main Content -->
      <main class=" w-full mx p-4 ">
        <slot/>
      </main>
      <RightSideBar class="lg:flex  hidden"/>

    </div>

    <!-- Footer -->
    <footer class=" text-white p-4">
      <div class="container mx-auto text-center">
        &copy; 2024 Your Company. All rights reserved.
      </div>
    </footer>
  </div>
</template>
