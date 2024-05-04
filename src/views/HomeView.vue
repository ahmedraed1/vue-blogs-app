<template>
  <main class="w-full h-screen flex flex-col">
    <div class="h-fit py-16 flex flex-col justify-center items-center gap-y-6">
      <h1 class="text-4xl">Dev.to Blog Posts</h1>
      <InputSearch />
    </div>
    <div class="basis-3/4">
      <div class="filter">
        <filterResults />
      </div>
      <div class="cards">
        <ResultsCards />
      </div>
    </div>
  </main>
</template>
<script setup>
import InputSearch from '../components/InputSearch.vue'
import filterResults from '../components/filterResults.vue'
import ResultsCards from '../components/ResultsCards.vue'
</script>
