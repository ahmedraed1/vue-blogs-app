<template>
  <section class="py-4">
    <div class="max-w-7xl mx-auto px-5 sm:px-10 md:px-12 lg:px-5 space-y-14">
      <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 gap-8">
        <div
          v-for="(item, index) in cards"
          :key="index"
          class="bg-white dark:bg-gray-950 border border-gray-100 dark:border-gray-900 px-px rounded-xl"
        >
          <div class="rounded-[11px] bg-gray-200 dark:bg-gray-800 relative">
            <img
              :src="item.social_image"
              alt="article cover"
              width="1400"
              class="rounded-[7px] w-full aspect-video object-cover"
            />
            <div
              class="absolute -bottom-8 z-10 flex inset-x-2 rounded-lg bg-gray-100 dark:bg-gray-900 border border-gray-200 dark:border-gray-800 p-2"
            >
              <div class="flex items-center gap-x-4">
                <img
                  :src="item.user.profile_image"
                  alt=""
                  width="800"
                  class="w-10 h-10 object-cover rounded-full"
                />
                <div>
                  <p class="text-gray-800 dark:text-gray-50 font-semibold">
                    By {{ item.user.name }}
                  </p>
                  <p class="text-sm text-gray-600 dark:text-gray-300">@{{ item.user.username }}</p>
                </div>
              </div>
            </div>
          </div>
          <div class="mt-14 px-5 pb-5 space-y-4">
            <span class="text-blue-600 dark:text-blue-400 text-sm">{{
              item.readable_publish_date + ' ' + item.created_at.slice(0, 4)
            }}</span>
            <h1 class="text-gray-900 dark:text-white text-xl font-semibold">
              {{ item.title }}
            </h1>
            <p class="text-gray-700 dark:text-gray-300 line-clamp-2">
              {{ item.description }}
            </p>
            <div class="w-full h-fit flex flex-row flex-wrap">
              <span class="block pl-2" v-for="(tag, index) in item.tag_list" :key="index"
                >#{{ tag }}</span
              >
            </div>
            <div class="flex flex-row justify-between">
              <a
                :href="item.url"
                class="w-fit flex items-center gap-x-2 text-blue-600 dark:text-blue-400"
              >
                Read more
                <svg
                  xmlns="http://www.w3.org/2000/svg"
                  viewBox="0 0 20 20"
                  fill="currentColor"
                  class="w-4 h-4"
                >
                  <path
                    fill-rule="evenodd"
                    d="M5.22 14.78a.75.75 0 001.06 0l7.22-7.22v5.69a.75.75 0 001.5 0v-7.5a.75.75 0 00-.75-.75h-7.5a.75.75 0 000 1.5h5.69l-7.22 7.22a.75.75 0 000 1.06z"
                    clip-rule="evenodd"
                  />
                </svg>
              </a>
              <div class="flex flex-row">
                {{ item.positive_reactions_count }}
                <img
                  width="30"
                  height="30"
                  src="https://img.icons8.com/ios-glyphs/30/C60000/like--v1.png"
                  alt="like--v1"
                  class="p-1"
                />
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>
<script setup>
import { ref, onMounted } from 'vue'
import axios from 'axios'

const cards = ref([])

onMounted(() => {
  axios
    .get(`https://dev.to/api/articles?tag=react`)
    .then((response) => (cards.value = response.data))
    .then(() => console.log(cards.value))
    .catch((error) => console.log(error))
})
</script>
