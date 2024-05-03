<template>
  <HeroImage @scroll-to-about="scrollToAbout" />
  <AboutView />
  <AwardView />
  <ServiceView />
  <BossView />
  <ExpView />
  <SlideView />
</template>

<script setup>
import HeroImage from '../components/HeroImage.vue'
import AboutView from '../components/AboutView.vue'
import AwardView from '../components/AwardView.vue'
import ServiceView from '../components/ServiceView.vue'
import BossView from '../components/BossView.vue'
import ExpView from '../components/ExpView.vue'
import SlideView from '../components/SlideView.vue'

import { gsap } from 'gsap'
import { ScrollToPlugin } from 'gsap/ScrollToPlugin'

gsap.registerPlugin(ScrollToPlugin)

const scrollToAbout = () => {
  gsap.to(window, {
    duration: 2, // 滾動動畫的持續時間（以秒為單位）
    scrollTo: '#about',
    ease: 'power1.inOut'
  })
}

</script>
