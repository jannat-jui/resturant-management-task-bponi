<script setup>
import { RouterLink, RouterView } from 'vue-router'
import HelloWorld from './components/HelloWorld.vue'
</script>

<template>
  <header>

    <div class="wrapper">
      <nav
        class=" bg-[#f5f4f2] border-b-2 shadow-sm fixed md:px-8 w-full z-50 p-4 h-20 flex justify-between items-center">
        <div class="flex items-center">
          <img src="./assets/lg-logo.png" alt="Logo" class="w-52 h-12 mr-2 hidden lg:block">
          <img src="./assets/small-logo.png" alt="Logo" class="w-8 md:w-20 h-12 mr-2 lg:hidden">

          <button
            class=" text-black px-2 md:px-4 py-2 rounded-xl text-xs md:text-lg border flex items-center gap-2 border-gray-300 bg-[#f2d700]">
            <img class="w-5" src="./assets/location-pin.png" alt="">Enter delivery address</button>
        </div>

        <div class="flex items-center">
          <button class="text-black px-4 py-2 rounded-md flex flex-col justify-center items-center"><img class="w-5"
              src="./assets/global.png" alt=""> English</button>


          <button class="bg-gray-200 text-black font-medium px-6 py-4 rounded-md ml-2">Login</button>
        </div>
      </nav>

    </div>
  </header>

  <RouterView />


</template>

