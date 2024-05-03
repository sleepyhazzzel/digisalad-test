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
              <VImg :src="service.image" />
            </div>
            <h4 class="card-title">{{ service.name }}</h4>
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
import { ref, onMounted, computed } from 'vue'
import { useDisplay } from 'vuetify'
import gsap from 'gsap'
import { ScrollTrigger } from 'gsap/ScrollTrigger'
import fruit0 from '../assets/fruit-0.png'
import fruit1 from '../assets/fruit-1.png'
import fruit2 from '../assets/fruit-2.png'
import fruit3 from '../assets/fruit-3.png'
import fruit4 from '../assets/fruit-4.png'
import fruit5 from '../assets/fruit-5.png'
import fruit6 from '../assets/fruit-6.png'
import fruit7 from '../assets/fruit-7.png'
import fruit8 from '../assets/fruit-8.png'

const services = ref([
  { name: 'ux design', image: fruit0 },
  { name: 'ui design', image: fruit1 },
  { name: 'website development', image: fruit2 },
  { name: 'mobile app development', image: fruit3 },
  { name: 'ecommerce', image: fruit4 },
  { name: 'customer loyalty', image: fruit5 },
  { name: 'digital transformation', image: fruit6 },
  { name: 'digital marketing', image: fruit7 },
  { name: 'branding', image: fruit8 }
])

const { smAndUp, lgAndUp } = useDisplay()
const isPad = computed(() => smAndUp.value)
const isDesktop = computed(() => lgAndUp.value)

gsap.registerPlugin(ScrollTrigger)

onMounted(() => {
  const cards = Array.from(document.querySelectorAll('.card'))
  let size = ''
  if (isDesktop.value) {
    size = 3
  } else if (isPad.value) {
    size = 2
  } else {
    size = 1
  }
  const groups = chunk(cards, size)

  groups.forEach((group, i) => {
    gsap.fromTo(group,
      { y: 100, opacity: 0 },
      {
        y: 0,
        opacity: 1,
        ease: 'power1.out',
        scrollTrigger: {
          trigger: group[0]
        },
        delay: i * 0.2 // 每組之間的動畫延遲時間（以秒為單位）
      }
    )
  })
})
function chunk (arr, size) {
  return Array.from({ length: Math.ceil(arr.length / size) }, (v, i) =>
    arr.slice(i * size, i * size + size)
  )
}
</script>
