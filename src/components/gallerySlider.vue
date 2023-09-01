<script setup lang="ts">
import sH from '@/components/sectionHeader.vue'
import {ref} from 'vue'

const images = ref<string[]>([
  new URL('/src/assets/slider1.png', import.meta.url).href,
  new URL('/src/assets/slider2.png', import.meta.url).href,
  new URL('/src/assets/slider3.png', import.meta.url).href,
])

</script>

<template>
  <div>
    <div class="d-flex justify-content-center">
      <sH txt="GALERIA"/>
    </div>
    <div id="gallerySlider" class="carousel slide">
      <div class="carousel-indicators" id="#gallerySlider">
        <button type="button" data-bs-target="#gallerySlider" data-bs-slide-to="0" class="active" aria-current="true" aria-label="Slide 1"></button>
        <button type="button" data-bs-target="#gallerySlider" data-bs-slide-to="1" aria-label="Slide 2"></button>
        <button type="button" data-bs-target="#gallerySlider" data-bs-slide-to="2" aria-label="Slide 3"></button>
      </div>
      <div class="carousel-inner">
        <div v-for="(image, index) in images" :key="index" :class="index === 0 ? 'carousel-item active' : 'carousel-item'">
        <img class="d-block w-100" :src="image" />
    </div>
      </div>
      <button class="carousel-control-prev" type="button" data-bs-target="#gallerySlider" data-bs-slide="prev">
        <span class="carousel-control-prev-icon" aria-hidden="true"></span>
        <span class="visually-hidden">Previous</span>
      </button>
      <button class="carousel-control-next" type="button" data-bs-target="#gallerySlider" data-bs-slide="next">
        <span class="carousel-control-next-icon" aria-hidden="true"></span>
        <span class="visually-hidden">Next</span>
      </button>
    </div>
  </div>
</template>