<template>
  <section id="slide">
    <Swiper
      class="swiper"
      :loop="true"
      :speed="2000"
      :navigation="true"
      :modules="modules"
      :slides-per-view="1"
      :space-between="50"
      :autoplay="{ delay: 3000, disableOnInteraction: false }"
    >
      <SwiperSlide v-for="(slide, i) in slides" :key="i" class="d-flex align-center">
        <div class="slide-bg" />
        <div v-if="isDesktop" class="pages">
          <div>0{{ i + 1 }}</div>
          <div class="slash ma-1" />
          <div class="total">0{{ slides.length }}</div>
        </div>
        <VRow justify="center" align="center" class="px-16">
          <VCol cols="10" sm="8" md="5" offset="0" style="position: relative;">
            <img :src="slide.image" class="left-img">
            <VBtn v-if="isDesktop" :href="slide.link" target="_blank" class="btn btn-desktop px-8 py-12" color="#26C6D0" rounded="0" size="x-large" flat>
              view project&nbsp;&nbsp;&nbsp;&nbsp;
              <div class="line" />
            </VBtn>
          </VCol>
          <VCol cols="10" sm="8" md="4" class="pa-6 ps-md-12">
            <div class="text-area">
              <div class="subtitle px-2">{{ slide.subtitle }}</div>
              <div v-if="isPad" class="d-flex align-center">
                <div class="slide-title my-4 px-2">{{ slide.title }}</div>
              </div>
              <div v-else class="slide-title-no-line my-4 px-2">{{ slide.title }}</div>
              <div class="text mt-4">{{ slide.content }}</div>
            </div>
            <VBtn v-if="!isDesktop" :href="slide.link" target="_blank" class="btn my-4 py-4" color="#26C6D0" rounded="0" size="x-large" flat>
              view project&nbsp;&nbsp;
              <div class="line" />
            </VBtn>
          </VCol>
        </VRow>
      </SwiperSlide>
    </Swiper>
  </section>
</template>

<script setup>
import { computed } from 'vue'
import { useDisplay } from 'vuetify'
import { Swiper, SwiperSlide } from 'swiper/vue'
import 'swiper/css'
import 'swiper/css/navigation'
import { Autoplay, Navigation } from 'swiper/modules'
import slideImage from '../assets/slide-1.png'

const { smAndUp, mdAndUp } = useDisplay()
const isPad = computed(() => smAndUp.value)
const isDesktop = computed(() => mdAndUp.value)

const modules = [Navigation]

const slides = [
  {
    title: 'LP CLUB MOBILE APP',
    subtitle: 'HIGHLIGHTED SHOWCASE',
    content: 'Cras quis nulla commodo, aliquam lectus sed, blandit augue. Cras ullamcorper bibendum bibendum. Duis tincidunt urna non pretium porta. Nam condimentum vitae ligula vel ornare. Phasellus at semper turpis. Nunc eu tellus tortor. Etiam at condimentum nisl, vitae sagittis orci. Donec id dignissim nunc. Donec elit ante, eleifend a dolor et, venenatis facilisis dolor. In feugiat orci odio, sed lacinia sem elementum quis. Aliquam consectetur, eros et vulputate euismod, nunc leo tempor lacus, ac rhoncus neque eros nec lacus. Cras lobortis molestie faucibus.',
    image: `${slideImage}`,
    link: 'https://www.google.com/'
  },
  {
    title: 'LP CLUB MOBILE APP',
    subtitle: 'HIGHLIGHTED SHOWCASE',
    content: 'Cras quis nulla commodo, aliquam lectus sed, blandit augue. Cras ullamcorper bibendum bibendum. Duis tincidunt urna non pretium porta. Nam condimentum vitae ligula vel ornare. Phasellus at semper turpis. Nunc eu tellus tortor. Etiam at condimentum nisl, vitae sagittis orci. Donec id dignissim nunc. Donec elit ante, eleifend a dolor et, venenatis facilisis dolor. In feugiat orci odio, sed lacinia sem elementum quis. Aliquam consectetur, eros et vulputate euismod, nunc leo tempor lacus, ac rhoncus neque eros nec lacus. Cras lobortis molestie faucibus.',
    image: `${slideImage}`,
    link: 'https://www.google.com/'
  },
  {
    title: 'LP CLUB MOBILE APP',
    subtitle: 'HIGHLIGHTED SHOWCASE',
    content: 'Cras quis nulla commodo, aliquam lectus sed, blandit augue. Cras ullamcorper bibendum bibendum. Duis tincidunt urna non pretium porta. Nam condimentum vitae ligula vel ornare. Phasellus at semper turpis. Nunc eu tellus tortor. Etiam at condimentum nisl, vitae sagittis orci. Donec id dignissim nunc. Donec elit ante, eleifend a dolor et, venenatis facilisis dolor. In feugiat orci odio, sed lacinia sem elementum quis. Aliquam consectetur, eros et vulputate euismod, nunc leo tempor lacus, ac rhoncus neque eros nec lacus. Cras lobortis molestie faucibus.',
    image: `${slideImage}`,
    link: 'https://www.google.com/'
  },
  {
    title: 'LP CLUB MOBILE APP',
    subtitle: 'HIGHLIGHTED SHOWCASE',
    content: 'Cras quis nulla commodo, aliquam lectus sed, blandit augue. Cras ullamcorper bibendum bibendum. Duis tincidunt urna non pretium porta. Nam condimentum vitae ligula vel ornare. Phasellus at semper turpis. Nunc eu tellus tortor. Etiam at condimentum nisl, vitae sagittis orci. Donec id dignissim nunc. Donec elit ante, eleifend a dolor et, venenatis facilisis dolor. In feugiat orci odio, sed lacinia sem elementum quis. Aliquam consectetur, eros et vulputate euismod, nunc leo tempor lacus, ac rhoncus neque eros nec lacus. Cras lobortis molestie faucibus.',
    image: `${slideImage}`,
    link: 'https://www.google.com/'
  }
]
</script>
