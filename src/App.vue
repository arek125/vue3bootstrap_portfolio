<script setup lang="ts">
  import { RouterView } from 'vue-router'
  import navBar from '@/components/navBar.vue'
  import { ref, provide } from 'vue'
    
  const sectionVisible = ref<any>({
    start: true,
    about: false,
    gallery: false
  })
  provide('sectionVisible', sectionVisible)
</script>

<template>
  <navBar  class="fixed-top" id="mainNavbar"/>
  <router-view ></router-view>
</template>
