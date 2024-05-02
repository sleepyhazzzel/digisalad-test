<template>
  <section id="service">
    <VContainer>
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
      <VRow class="my-6">
        <VCol v-for="(service, i) in services" :key="i" cols="12" sm="6" md="4">
          <div class="card pa-2">
            <div class="fruit">
              <VImg :src="`https://github.com/sleepyhazzzel/digisalad-test/blob/main/src/assets/fruit-${i}.png?raw=true`" />
            </div>
            <h4 class="card-title">{{ service }}</h4>
            <div class="text" style="color: #fff;">
              Cras quis nulla commodo, aliquam lectus sed, blandit augue. Cras ullamcorper bibendum bibendum. Duis tincidunt urna non pretium porta. Nam condimentum vitae ligula vel ornare.
            </div>
            <VBtn variant="outlined" rounded="pill" color="#fff" :text="service === 'branding' ? 'branding' : 'view more'" class="round-btn my-10" />
          </div>
        </VCol>
      </VRow>
      <div id="quote" class="mb-16">view more digidalad's ingradients</div>
    </VContainer>
  </section>
</template>

<script setup>
import { ref } from 'vue'

const services = ref(['ux design', 'ui design', 'website development', 'mobile app development', 'ecommerce', 'customer loyalty', 'digital transformation', 'digital marketing', 'branding'])
</script>
