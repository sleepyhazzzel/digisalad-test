<template>
  <section id="hero" style="margin-top: -120px;">
    <div id="video-container">
      <iframe src="https://www.youtube.com/embed/8_4JRK4QkqU?autoplay=1&mute=1&playsinline=1&loop=1&playlist=8_4JRK4QkqU&controls=0&disablekb=1" allowfullscreen allow="accelerometer; autoplay; encrypted-media; gyroscope; picture-in-picture" frameBorder="0" />
    </div>
    <div id="overlay">
      <div class="left">
        <div class="rotate">
          <div class="side-text">digital agency</div>
        </div>
      </div>
      <div class="center">
        <img class="logo" src="../assets/salad-logo.png" alt="logo">
        <h1 class="quote">We create<br>amazing<br>digital experiences</h1>
      </div>
      <div class="bottom">
        <img id="salad" src="../assets/salad.png" alt="salad" @click="$emit('scroll-to-about')">
      </div>
      <div class="bottom-line">
        <div class="line" />
      </div>
    </div>
  </section>
</template>

<script setup>
import { onMounted } from 'vue'
import gsap from 'gsap'

defineEmits(['scroll-to-about'])

onMounted(() => {
  gsap.to('#salad', {
    y: '-=15',
    repeat: -1,
    yoyo: true,
    ease: 'power1.inOut',
    duration: 1
  })
})
</script>
