<script setup lang="ts">
import { onMounted } from 'vue'
import Card from './components/Card.vue'

onMounted(() => {
  document.body.style.setProperty('--mx', -100 + 'px')
  document.body.style.setProperty('--my', -100 + 'px')
  window.addEventListener('mousemove', e => {
    document.body.style.setProperty('--mx', e.clientX + 'px')
    document.body.style.setProperty('--my', e.clientY + 'px')
  })
})
</script>

<template>
  <div class="container">
    <Card/>
    <Card/>
    <Card/>
    <Card/>
    <Card/>
    <Card/>
    <Card/>
    <Card/>
  </div>
</template>

<style scoped lang="scss">
.container {
  display: flex;
  gap: 16px;
  flex-wrap: wrap;
  max-width: 1000px;
}
</style>

