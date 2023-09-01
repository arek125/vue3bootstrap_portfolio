<script setup lang="ts">
    import aboutMe from '@/components/aboutMe.vue'
    import gallerySlider from '@/components/gallerySlider.vue'
    import contactModal from "@/components/contactModal.vue"
    import { useIntersectionObserver } from '@vueuse/core'
    import { ref, inject } from 'vue'
    
    const sectionVisible:any = inject('sectionVisible')

    const start = ref(null)
    const about = ref(null)
    const gallery = ref(null)
    
    setTimeout(()=>{
      useIntersectionObserver(
        start,
      ([{ isIntersecting }]) => {
        if(isIntersecting)sectionVisible.value.start = true
        else sectionVisible.value.start = false
      }
    )
      useIntersectionObserver(
        about,
      ([{ isIntersecting }]) => {
        if(isIntersecting)sectionVisible.value.about = true
        else sectionVisible.value.about = false
      }
    )
      useIntersectionObserver(
        gallery,
      ([{ isIntersecting }]) => {
        if(isIntersecting)sectionVisible.value.gallery = true
        else sectionVisible.value.gallery = false
      }
    )
    },1000)

</script>

<template>
  <div class="main-container" style="margin-top: 78px;" >
    <div class="my-b" >
        <img src="@/assets/start.png" ref="start" class="img-fluid" alt="Logo">
    </div>

    <div id="about" class="py-5"></div>  

    <div class="my-5">
        <aboutMe ref="about"/>
    </div>

    <div id="gallery" class="py-5"></div>  

    <div class="my-5">
        <gallerySlider ref="gallery"/>
    </div>

    <div class="footer"></div>
    <contactModal/>
  </div>
</template>

<style scoped lang="scss">
.footer{
  width: 100%;
  height: 200px;
  background-color: var(--bs-secondary);;
}
</style>