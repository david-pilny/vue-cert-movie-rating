<script setup>
import { items } from './movies.json'
import { StarIcon } from '@heroicons/vue/24/solid'
</script>

<template>
  <!-- This is where your template goes	-->
  <div class="flex flex-row justify-center items-center space-x-8">
    <div
      v-for="(item, index) in items"
      :key="index"
      class="max-w-sm bg-white rounded-lg shadow"
    >
      <div class="object-contain h-15">
        <img class="rounded-t-lg" :src="item.image" alt="" />
      </div>

      <div>
        <div class="p-5">
          <a href="#">
            <h5
              class="mb-2 text-2xl tracking-tight text-gray-900 dark:text-black"
            >
              {{ item.name }}
            </h5>
          </a>

          <div class="mb-4">
            <span
              v-for="(genre, index) in item.genres"
              :key="index"
              class="bg-blue-100 text-white text-sm font-medium me-2 px-2.5 py-0.5 rounded-full dark:bg-indigo-700 dark:text-white"
              >{{ genre }}</span
            >
          </div>

          <p class="mb-10 font-normal text-gray-700 dark:text-black">
            {{ item.description }}
          </p>
          <p>Rating: ({{ item.rating }}/5)</p>
        </div>
      </div>
    </div>
  </div>
</template>
