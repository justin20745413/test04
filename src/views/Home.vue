<template>
  <q-page class="flex flex-center">
    <div class="tw-container tw-mx-auto tw-p-4">
      <h1 class="tw-text-2xl tw-font-bold tw-mb-4">Welcome to Test03</h1>
      <div class="row q-col-gutter-md">
        <!-- Counter Example -->
        <div class="col-12 col-md-6">
          <q-card>
            <q-card-section>
              <div class="text-h6">Counter: {{ store.count }}</div>
              <q-btn color="primary" @click="store.increment">Increment</q-btn>
            </q-card-section>
          </q-card>
        </div>

        <!-- Swiper Example -->
        <div class="col-12">
          <swiper
            :slides-per-view="3"
            :space-between="30"
            @swiper="onSwiper"
            @slideChange="onSlideChange"
          >
            <swiper-slide v-for="n in 5" :key="n">Slide {{ n }}</swiper-slide>
          </swiper>
        </div>
      </div>
    </div>
  </q-page>
</template>

<script setup lang="ts">
import { onMounted } from 'vue'
import { useMainStore } from '../stores'

import 'swiper/css'

const store = useMainStore()

onMounted(() => {
  gsap.from('h1', {
    y: -50,
    opacity: 0,
    duration: 1
  })
})

const onSwiper = (swiper: any) => {
  console.log(swiper)
}

const onSlideChange = () => {
  console.log('slide change')
}
</script>

<style lang="scss" scoped>
.swiper {
  width: 100%;
  height: 200px;
  .swiper-slide {
    display: flex;
    justify-content: center;
    align-items: center;
    background: $primary;
    color: white;
    border-radius: 8px;
  }
}
</style>
