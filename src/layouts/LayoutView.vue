<template>
  <VAppBar scroll-behavior="fade-image inverted" color="rgba(255, 255, 255, 0)" :height="appBarHeight" flat>
    <template #image>
      <VImg gradient="#fff, #fff" />
    </template>
    <div id="navbar">
      <div v-if="isDesktop" id="nav-btn" class="rounded-pill">
        start your project
      </div>
      <div id="hamberger">
        <div :class="isScrolling ? 'line-gray' : 'line-white'" />
        <div :class="isScrolling ? 'line-gray' : 'line-white'" />
        <div :class="isScrolling ? 'line-gray' : 'line-white'" />
      </div>
    </div>
  </VAppBar>
  <VMain>
    <RouterView />
  </VMain>
</template>

<script setup>
import { ref, computed, onMounted } from 'vue'
import { useDisplay } from 'vuetify'

const { smAndUp } = useDisplay()
const isDesktop = computed(() => smAndUp.value)

const appBarHeight = ref(120) // 初始高度
const isScrolling = ref(false)

const onScroll = () => {
  appBarHeight.value = Math.max(66, 120 - window.scrollY)
  if (appBarHeight.value < 80) {
    isScrolling.value = true
  } else {
    isScrolling.value = false
  }
}

onMounted(() => {
  window.addEventListener('scroll', onScroll)
})
</script>
