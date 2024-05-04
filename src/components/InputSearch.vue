<template>
  <div class="flex items-start">
    <div class="flex flex-col relative">
      <button
        id="dropdown-button"
        data-dropdown-toggle="dropdown"
        class="flex-shrink-0 z-10 inline-flex items-center py-2.5 px-4 text-sm font-medium text-center text-gray-900 bg-gray-100 border border-e-0 border-gray-300 dark:border-gray-700 dark:text-white rounded-s-lg hover:bg-gray-200 focus:ring-4 focus:outline-none focus:ring-gray-300 dark:bg-gray-600 dark:hover:bg-gray-700 dark:focus:ring-gray-800"
        type="button"
        @click="openSearchTypes"
      >
        {{ searchType }}
        <svg
          class="w-2.5 h-2.5 ms-2.5"
          aria-hidden="true"
          xmlns="http://www.w3.org/2000/svg"
          fill="none"
          viewBox="0 0 10 6"
        >
          <path
            stroke="currentColor"
            stroke-linecap="round"
            stroke-linejoin="round"
            stroke-width="2"
            d="m1 1 4 4 4-4"
          />
        </svg>
      </button>
      <div
        id="dropdown"
        class="absolute top-11 hidden z-10 bg-white divide-y divide-gray-100 rounded-lg shadow w-44 dark:bg-gray-700"
      >
        <ul class="py-2 text-sm text-gray-700 dark:text-gray-200" aria-labelledby="dropdown-button">
          <li>
            <button
              :disabled="searchType == 'All categories'"
              class="w-full text-start block px-4 py-2 hover:bg-gray-100 dark:hover:bg-gray-600 dark:hover:text-white"
              @click="addSearchType('All categories')"
            >
              All categories
            </button>
          </li>
          <li>
            <button
              :disabled="searchType == 'Shopping'"
              class="w-full text-start block px-4 py-2 hover:bg-gray-100 dark:hover:bg-gray-600 dark:hover:text-white"
              @click="addSearchType('Shopping')"
            >
              Vue
            </button>
          </li>
          <li>
            <button
              :disabled="searchType == 'Images'"
              class="w-full text-start block px-4 py-2 hover:bg-gray-100 dark:hover:bg-gray-600 dark:hover:text-white"
              @click="addSearchType('Images')"
            >
              React
            </button>
          </li>
          <li>
            <button
              :disabled="searchType == 'News'"
              class="w-full text-start block px-4 py-2 hover:bg-gray-100 dark:hover:bg-gray-600 dark:hover:text-white"
              @click="addSearchType('News')"
            >
              Javascript
            </button>
          </li>
          <li>
            <button
              :disabled="searchType == 'Finance'"
              class="w-full text-start block px-4 py-2 hover:bg-gray-100 dark:hover:bg-gray-600 dark:hover:text-white"
              @click="addSearchType('Finance')"
            >
              Database
            </button>
          </li>
        </ul>
      </div>
    </div>
    <div class="relative w-30">
      <input
        type="search"
        id="search-dropdown"
        class="block p-2.5 w-full z-20 text-sm text-gray-900 bg-gray-50 rounded-e-lg rounded-s-gray-100 rounded-s-2 border border-gray-300 focus:ring-blue-500 focus:border-blue-500 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:border-blue-500"
        placeholder="Search"
        v-model="searchValue"
        required
      />
      <button
        type="submit"
        class="absolute top-0 end-0 p-2.5 h-full text-sm font-medium text-white bg-blue-700 rounded-e-lg border border-blue-700 hover:bg-blue-800 focus:ring-4 focus:outline-none focus:ring-blue-300 dark:bg-blue-600 dark:hover:bg-blue-700 dark:focus:ring-blue-800"
      >
        <svg
          class="w-4 h-4"
          aria-hidden="true"
          xmlns="http://www.w3.org/2000/svg"
          fill="none"
          viewBox="0 0 20 20"
        >
          <path
            stroke="currentColor"
            stroke-linecap="round"
            stroke-linejoin="round"
            stroke-width="2"
            d="m19 19-4-4m0-7A7 7 0 1 1 1 8a7 7 0 0 1 14 0Z"
          />
        </svg>
      </button>
    </div>
  </div>
</template>
<script setup>
import { ref } from 'vue'

const searchValue = ref('')
const searchType = ref('All categories')

const addSearchType = function (value) {
  searchType.value = value
  document.getElementById('dropdown').classList.add('hidden')
}

const openSearchTypes = function () {
  document.getElementById('dropdown').classList.toggle('hidden')
}
</script>
<style scoped>
.w-30 {
  width: 30rem;
}
</style>
