<template>
  <div id="service">
    <VContainer>
      <div class="space" />
      <div class="d-flex justify-center my-16">
        <div class="title" style="color: #fff;">
          our ingradients
          <div class="underline-p-0" />
          <div class="underline-p-1" />
        </div>
      </div>
      <p class="text px-6" style="color: #fff;">
        Cras quis nulla commodo, aliquam lectus sed, blandit augue. Cras ullamcorper bibendum bibendum. Duis tincidunt urna non pretium porta. Nam condimentum vitae ligula vel ornare. Phasellus at semper turpis. Nunc eu tellus tortor. Etiam at condimentum nisl, vitae sagittis orci. Donec id dignissim nunc. Donec elit ante, eleifend a dolor et, venenatis facilisis dolor. In feugiat orci odio, sed lacinia sem elementum quis. Aliquam consectetur, eros et vulputate euismod, nunc leo tempor lacus, ac rhoncus neque eros nec lacus. Cras lobortis molestie faucibus.
      </p>
      <VBtn class="btn my-8 py-8" color="#585880" rounded="0" size="x-large" flat>
        our services&nbsp;
        <span class="line" />
      </VBtn>
      <VRow>
        <VCol v-for="(service, i) in services" :key="i" cols="12" sm="6" md="4">
          <div class="card pa-2">
            <div class="fruit">
              <VImg :src="service.image" />
            </div>
            <h4 class="card-title">{{ service.title }}</h4>
            <div class="text" style="color: #fff;">
              Cras quis nulla commodo, aliquam lectus sed, blandit augue. Cras ullamcorper bibendum bibendum. Duis tincidunt urna non pretium porta. Nam condimentum vitae ligula vel ornare.
            </div>
            <VBtn variant="outlined" rounded="xl" color="#fff">view more</VBtn>
          </div>
        </VCol>
      </VRow>
    </VContainer>
  </div>
</template>

<script setup>
import { ref } from 'vue'

for (let i = 0; i < 9; i++) {
  import(`@/assets/fruit-${i}.png`)
}

const services = ref([
  {
    image: '../assets/fruit-0.png',
    title: 'ux design'
  },
  {
    image: '../assets/fruit-1.png',
    title: 'ui design'
  },
  {
    image: '../assets/fruit-2.png',
    title: 'website development'
  },
  {
    image: '../assets/fruit-3.png',
    title: 'mobile app development'
  },
  {
    image: '../assets/fruit-4.png',
    title: 'ecommerce'
  },
  {
    image: '../assets/fruit-5.png',
    title: 'customer loyalty'
  },
  {
    image: '../assets/fruit-6.png',
    title: 'digital transformation'
  },
  {
    image: '../assets/fruit-7.png',
    title: 'digital marketing'
  },
  {
    image: '../assets/fruit-8.png',
    title: 'branding'
  }
])
</script>
