<script lang="ts" setup>
import { toRefs } from 'vue'

import BaseButton from './common/BaseButton.vue'

const emit = defineEmits(['addMovie'])

const props = defineProps<{
  totalMovies: number
  averageRating: number
}>()

const { totalMovies, averageRating } = toRefs(props)
</script>

<template>
  <nav class="navbar">
    <ul class="navbar-text">
      <li>Total Movies: {{ totalMovies }}</li>
      <li>/</li>
      <li>Average rating: {{ averageRating }}</li>
    </ul>

    <ul class="flex flex-row justify-between w-[25%]">
      <li>
        <BaseButton class="button">Remove Rating</BaseButton>
      </li>
      <li>
        <BaseButton class="button" @click="emit('addMovie')"
          >Add Movie</BaseButton
        >
      </li>
    </ul>
  </nav>
</template>

<style scoped>
@tailwind base;
@tailwind components;
@tailwind utilities;

.navbar {
  @apply mb-[25px] pt-10 flex flex-row justify-between w-9/12;
}

.navbar-text {
  @apply flex flex-row text-white items-center justify-between w-[25%];
}

.button {
  @apply bg-cyan-500 hover:bg-cyan-700 text-white;
}

@media screen and (min-width: 1800px) {
  .navbar-text {
    @apply flex flex-row text-white items-center justify-between w-[20%];
  }
}
</style>
