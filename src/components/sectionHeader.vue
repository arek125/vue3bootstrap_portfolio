<script setup lang="ts">
defineProps({
    txt: String
})

</script>

<template>
    <div>
        <h1>{{ txt }}</h1>
        <hr class="solid">
    </div>
</template>

<style scoped>
h1 {
    font-weight: 900;
    letter-spacing: 0.2em
}
</style>