<template>
  <VAppBar scroll-behavior="fade-image inverted" color="rgba(255, 255, 255, 0)" :height="appBarHeight" flat>
    <template #image>
      <VImg gradient="#fff, #fff" />
    </template>
    <div id="navbar">
      <div v-if="isPad" id="nav-btn" class="rounded-pill">
        start your project
      </div>
      <div id="hamberger" @click="dialog = true">
        <div :class="isScrolling ? 'line-gray' : 'line-white'" />
        <div :class="isScrolling ? 'line-gray' : 'line-white'" />
        <div :class="isScrolling ? 'line-gray' : 'line-white'" />
      </div>
    </div>
  </VAppBar>
  <VDialog v-model="dialog" transition="dialog-top-transition" fullscreen>
    <VCard flat>
      <VImg :src="sideMenuBg" gradient="to bottom, rgba(88, 88, 128, .9), rgba(38, 198, 208, .9)" cover>
        <VRow justify="space-between" align-content="center" class="mt-6">
          <VCol cols="4" sm="3" lg="2" class="ms-6">
            <VImg :src="saladLogo" height="65" />
          </VCol>
          <VCol cols="3" sm="2" lg="1" class="text-center me-6">
            <VBtn icon variant="text" color="#fff" size="x-large" flat @click="dialog = false">
              <VIcon size="45" color="#fff">mdi-close</VIcon>
            </VBtn>
          </VCol>
        </VRow>
        <VRow v-if="isDesktop" justify="center" align="center" class="mx-0 mx-md-16 my-0 center" no-gutters>
          <VCol v-for="component in components" :key="component" cols="12" :md="component.md" class="pa-0">
            <VRow :id="component.id">
              <VCol v-for="card in component.cards" :key="card" cols="12" class="px-4 py-5">
                <VCard rounded="xl" flat @click="scrollToAnchor(card.anchor)">
                  <VImg
                    class="pa-8 d-flex align-end"
                    :src="card.image"
                    :height="card.height"
                    :gradient="`${card.color}, ${card.color}`"
                    cover
                  >
                    <VRow>
                      <VCol :cols="card.iconCols">
                        <VImg :src="card.icon" :height="card.iconHeight" position="left 50%" />
                      </VCol>
                      <VCol :cols="card.textCols">
                        <div class="card-subtitle" :style="`color: ${card.subtitleColor}`">{{ card.subtitle }}</div>
                        <span class="card-title" :style="`color: ${card.titleColor}`">
                          {{ card.title }}
                          <div class="dot" />
                        </span>
                      </VCol>
                    </VRow>
                  </VImg>
                </VCard>
              </VCol>
            </VRow>
          </VCol>
        </VRow>
        <VRow v-else class="ma-3" no-gutters>
          <VCol v-for="card in cards" :key="card" cols="6" class="pa-2">
            <VCard :loaction="card.anchor" rounded="xl" flat>
              <VImg
                class="pa-4 pa-sm-8 d-flex align-end"
                :src="card.image"
                height="25vh"
                :gradient="`${card.color}, ${card.color}`"
                cover
              >
                <div class="card-subtitle" :style="`color: ${card.subtitleColor}`">{{ card.subtitle }}</div>
                <span class="card-title" :style="`color: ${card.titleColor}`">
                  {{ card.title }}
                  <div class="dot" />
                </span>
              </VImg>
            </VCard>
          </VCol>
        </VRow>
      </VImg>
    </VCard>
  </VDialog>
  <VMain>
    <RouterView />
  </VMain>
</template>

<script setup>
import { ref, computed, onMounted, nextTick } from 'vue'
import { useDisplay } from 'vuetify'
import sideMenuBg from '../assets/side-menu-bg.png'
import saladLogo from '../assets/salad-logo.png'
import leaf from '../assets/fruit-0.png'
import cheese from '../assets/fruit-2.png'
import carrot from '../assets/fruit-9.png'
import tomato from '../assets/fruit-1.png'
import cucumber from '../assets/fruit-10.png'
import bgAbout from '../assets/bg-about.png'
import bgCareers from '../assets/bg-careers.png'
import bgInsights from '../assets/bg-insights.png'
import bgServices from '../assets/bg-services.png'
import bgWorks from '../assets/bg-works.png'

const { smAndUp, lgAndUp } = useDisplay()
const isPad = computed(() => smAndUp.value)
const isDesktop = computed(() => lgAndUp.value)

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

const dialog = ref(false)

const cards = ref([
  {
    title: 'About Us',
    subtitle: 'empowering brands',
    image: `${bgAbout}`,
    icon: `${leaf}`,
    color: 'rgba(38, 198, 208, 0.8)',
    height: 210,
    anchor: 'about'
  },
  {
    title: 'Works',
    subtitle: 'case studies',
    image: `${bgWorks}`,
    icon: `${tomato}`,
    color: 'rgba(238, 108, 138, 0.8)',
    height: 320,
    anchor: 'slide'
  },
  {
    title: 'Careers',
    subtitle: 'be cool with us',
    image: `${bgCareers}`,
    icon: `${cheese}`,
    color: 'rgba(230, 169, 78, 0.8)',
    height: 430,
    anchor: 'exp'
  },
  {
    title: 'Insights',
    subtitle: 'our strategies',
    image: `${bgAbout}`,
    icon: `${cucumber}`,
    color: 'rgba(38, 208, 168, 0.8)',
    height: 282,
    anchor: 'boss'
  },
  {
    title: 'Services',
    subtitle: 'area of expertise',
    image: `${bgServices}`,
    icon: `${carrot}`,
    color: 'rgba(88, 88, 128, 0.8)',
    height: 320,
    anchor: 'service'
  },
  {
    title: 'Contact',
    subtitle: 'start your journey with us',
    image: `${bgInsights}`,
    icon: '',
    color: 'rgba(255, 255, 255, 1)',
    titleColor: '#26C6D0',
    subtitleColor: '#262626',
    height: 210,
    anchor: ''
  }
])

const components = ref([
  {
    id: 'row0',
    md: 4,
    cards: [
      {
        title: 'About Us',
        subtitle: 'empowering brands',
        image: `${bgAbout}`,
        icon: `${leaf}`,
        iconHeight: 65,
        iconCols: 3,
        textCols: 9,
        color: 'rgba(38, 198, 208, 0.8)',
        height: 210,
        anchor: 'about'
      },
      {
        title: 'Works',
        subtitle: 'case studies',
        image: `${bgWorks}`,
        icon: `${tomato}`,
        iconHeight: 60,
        iconCols: 3,
        textCols: 9,
        color: 'rgba(238, 108, 138, 0.8)',
        height: 320,
        anchor: 'slide'
      }
    ]
  },
  {
    id: 'row1',
    md: 3,
    cards: [
      {
        title: 'Careers',
        subtitle: 'be cool with us',
        image: `${bgCareers}`,
        icon: `${cheese}`,
        iconHeight: 50,
        iconCols: 12,
        textCols: 12,
        color: 'rgba(230, 169, 78, 0.8)',
        height: 430,
        anchor: 'exp'
      },
      {
        title: 'Insights',
        subtitle: 'our strategies',
        image: `${bgAbout}`,
        icon: `${cucumber}`,
        iconHeight: 80,
        iconCols: 12,
        textCols: 12,
        color: 'rgba(38, 208, 168, 0.8)',
        height: 282,
        anchor: 'boss'
      }
    ]
  },
  {
    id: 'row2',
    md: 4,
    cards: [
      {
        title: 'Services',
        subtitle: 'area of expertise',
        image: `${bgServices}`,
        icon: `${carrot}`,
        iconHeight: 60,
        iconCols: 12,
        textCols: 12,
        color: 'rgba(88, 88, 128, 0.8)',
        height: 320,
        anchor: 'service'
      },
      {
        title: 'Contact',
        subtitle: 'start your journey with us',
        image: `${bgInsights}`,
        icon: '',
        iconCols: 12,
        textCols: 12,
        color: 'rgba(255, 255, 255, 1)',
        titleColor: '#26C6D0',
        subtitleColor: '#262626',
        height: 210,
        anchor: ''
      }
    ]
  }
])

const scrollToAnchor = (anchor) => {
  dialog.value = false
  const el = document.getElementById(anchor)
  if (el) {
    nextTick(() => {
      el.scrollIntoView({ behavior: 'smooth' })
    })
  }
}
</script>

<style scoped lang="sass">
:deep(.v-toolbar__content)
    align-items: center !important
</style>
