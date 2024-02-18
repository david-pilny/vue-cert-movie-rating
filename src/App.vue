<script setup>
import { reactive } from 'vue'
import { StarIcon } from '@heroicons/vue/24/solid'
import { items } from './movies.json'

const movies = reactive(items)
</script>

<template>
  <div class="app">
    <div class="movie-list">
      <div class="movie-item" v-for="movie in movies" :key="movie.id">
        <div class="movie-item-image-wrapper">
          <img :src="movie.image" class="movie-item-image" alt="" />
          <div class="movie-item-rating-badge">
            <div class="icon-number-wrapper">
              <StarIcon class="movie-item-star-icon-corner" />
              <span class="movie-item-rating-number">{{ movie.rating }}</span>
            </div>
          </div>
        </div>

        <div class="movie-item-content-wrapper">
          <div class="movie-item-title-wrapper">
            <h3 class="movie-item-title">{{ movie.name }}</h3>
            <div class="movie-item-genres-wrapper">
              <span
                v-for="genre in movie.genres"
                :key="`${movie.id}-${genre}`"
                class="movie-item-genre-tag"
                >{{ genre }}</span
              >
            </div>
          </div>
          <div class="movie-item-description-wrapper">
            <p class="movie-item-description">{{ movie.description }}</p>
          </div>
          <div class="movie-item-rating-wrapper">
            <span class="movie-item-rating-text">
              Rating: ({{ movie.rating }}/5)
            </span>
            <template v-for="star in 5" :key="`star-${star}`">
              <StarIcon
                v-if="star == movie.rating"
                class="movie-item-star-icon-yellow not-allowed"
              />
              <StarIcon
                v-else
                :class="
                  star <= movie.rating
                    ? 'movie-item-star-icon-yellow'
                    : 'movie-item-star-icon-gray'
                "
                @click="() => (movie.rating = star)"
              />
            </template>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
