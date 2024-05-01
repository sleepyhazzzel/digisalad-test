<template>
  <section id="award">
    <VContainer class="my-6 my-sm-8 my-lg-14 ps-6">
      <div class="d-flex">
        <div class="title ms-6">
          awards
          <div class="underline-0" />
        </div>
      </div>
      <VRow>
        <VCol cols="12" md="5" class="pe-10">
          <p class="my-12 text">
            Cras quis nulla commodo, aliquam lectus sed, blandit augue. Cras ullamcorper bibendum bibendum. Duis tincidunt urna non pretium porta. Nam condimentum vitae ligula vel ornare. Phasellus at semper turpis. Nunc eu tellus tortor. Etiam at condimentum nisl, vitae sagittis orci. Donec id dignissim nunc.
          </p>
        </VCol>
        <VCol v-for="i in 2" :key="i" cols="12" md="3" class="text-center pe-8 pe-md-0">
          <img src="../assets/award.png">
          <img src="../assets/award.png">
        </VCol>
      </VRow>
    </VContainer>
  </section>
</template>

<script setup>
</script>
