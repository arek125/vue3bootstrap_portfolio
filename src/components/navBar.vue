
<script setup lang="ts">
    import { inject } from 'vue'
    const sectionVisible:any = inject('sectionVisible')
</script>

<template>
    <nav class="navbar px-3" >
      <div class="container-xl justify-content-between">
        <div class="d-flex justify-content-start">
            <img src="@/assets/logoww.svg" class="img-fluid" style="height: 60px;">
            <ul class="nav nav-pills d-none d-lg-flex" style="margin-top: 10px;">
                <li  class="nav-item mx-3" >
                    <router-link :class="sectionVisible.start? 'active':''" class="nav-link" :to="{ path: '/' }">START</router-link>
                </li>
                <li  class="nav-item mx-3">
                    <router-link :class="sectionVisible.about? 'active':''" class="nav-link" :to="{ path: '/', hash: '#about' }">O MNIE</router-link>
                </li>
                <li  class="nav-item mx-3">
                    <router-link :class="sectionVisible.gallery? 'active':''" class="nav-link" :to="{ path: '/', hash: '#gallery' }">GALERIA</router-link>
                </li>
                <li class="nav-item mx-3" style="cursor: pointer">
                    <a class="nav-link" data-bs-toggle="modal" data-bs-target="#contactModalCenter">KONTAKT</a>
                </li>
            </ul>
        </div>
        <div>
            <img src="@/assets/facebook.svg" class="img-fluid rightIcon">
            <img src="@/assets/instagram.svg" class="img-fluid rightIcon">
            <img src="@/assets/youtube.svg" class="img-fluid rightIcon">
        </div>

        <button class="navbar-toggler d-lg-none" type="button" data-bs-toggle="collapse" data-bs-target="#navbarSupportedContent" aria-controls="navbarSupportedContent" aria-expanded="false" aria-label="Toggle navigation">
          <span class="navbar-toggler-icon"></span>
        </button>
        <div class="collapse navbar-collapse main-nav-bar " id="navbarSupportedContent">
          <ul class="navbar-nav ms-auto me-auto mb-2 mb-lg-0 ">
            <li  class="nav-item mx-3" >
                <router-link :class="sectionVisible.start? 'active':''" class="nav-link" :to="{ path: '/', hash: '#start' }">START</router-link>
            </li>
            <li  class="nav-item mx-3">
                <router-link :class="sectionVisible.about? 'active':''" class="nav-link" :to="{ path: '/', hash: '#about' }">O MNIE</router-link>
            </li>
            <li  class="nav-item mx-3">
                <router-link :class="sectionVisible.gallery? 'active':''" class="nav-link" :to="{ path: '/', hash: '#gallery' }">GALERIA</router-link>
            </li>
            <li class="nav-item mx-3" style="cursor: pointer">
                <a class="nav-link" data-bs-toggle="modal" data-bs-target="#contactModalCenter">KONTAKT</a>
            </li>
          </ul>
        </div>
      </div>
    </nav>
</template>

<style scoped>

.rightIcon{
    height: 40px;
    filter: opacity(0.3);
    margin-right: 10px;
}

</style>