<template>
  <VCarousel>
    <VCarouselSlide v-for="slide in slides" :key="slide.title">
      <img :src="slide.image" alt="slide">
      <VCarouselSlideContent>
        <h2>{{ slide.title }}</h2>
        <p>{{ slide.subtitle }}</p>
      </VCarouselSlideContent>
    </VCarouselSlide>
  </VCarousel>
</template>

<script setup>
import { ref } from 'vue'

const slides = ref([
  {
    title: 'Slide 1',
    subtitle: 'Subtitle 1',
    image: 'https://via.placeholder.com/800x400'
  },
  {
    title: 'Slide 2',
    subtitle: 'Subtitle 2',
    image: 'https://via.placeholder.com/800x400'
  },
  {
    title: 'Slide 3',
    subtitle: 'Subtitle 3',
    image: 'https://via.placeholder.com/800x400'
  }
])
</script>
