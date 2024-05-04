<template>
  <!-- <header class="w-full h-fit py-1 px-10 flex flex-row justify-between">
    <div>
      <img src="/public/favicon.ico" alt="" srcset="" />
    </div>
    <div>
      <ul class="h-full list-none flex flex-row gap-x-6 items-center text-black">
        <li>content</li>
        <li>About</li>
        <li>Info</li>
      </ul>
    </div>
  </header> -->
  <RouterView />
</template>
<script setup>
import { RouterView } from 'vue-router'
</script>

<style scoped></style>
