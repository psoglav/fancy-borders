<script setup lang="ts">
import {onMounted,ref} from 'vue'

const root = ref<HTMLDivElement>()

onMounted(() => {
  const rect = root.value?.getBoundingClientRect()
  root.value?.style.setProperty('--x', rect?.left + 'px')
  root.value?.style.setProperty('--y', rect?.top + 'px')
})
</script>

<template>
  <div class="card" ref="root">
    <div class="card-border">
      <div class="cursor"></div>
    </div>
    <div class="card-content">
      <p>
        Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore
        magna aliqua.
      </p>
      <div class="card-actions">
        <div class="button">
          Get Started
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped lang="scss">
.card {
  width: 200px;
  height: 300px;
  position: relative;
  background: #070808;
  overflow: hidden;

  &-content {
    position: relative;
    padding: 24px;
    display: flex;
    justify-content: space-between;
    flex-direction: column;
    height: 100%;
    font-size: 14px;
  }

  &-border {
    --width: 2px;
    position: absolute;
    z-index: 1;
    width: 100%;
    height: 100%;
    inset: 0;
    // background: #ffffff11;
    backdrop-filter: blur(80px);
    pointer-events: none;
    filter: saturate(3);
    clip-path: polygon(
        evenodd,
        0 0,
        100% 0,
        100% 100%,
        0 100%,
        0 0,
        var(--width) var(--width),
        calc(100% - var(--width)) var(--width),
        calc(100% - var(--width)) calc(100% - var(--width)),
        var(--width) calc(100% - var(--width)),
        var(--width) var(--width)
    );

    .cursor {
      position: fixed;
      left: calc(var(--mx) - var(--x));
      top: calc(var(--my) - var(--y));
      width: 20px;
      height: 20px;
      background: #fff;
      filter: blur(20px);
    }
  }
}

.button {
  cursor: pointer;
  padding: 0.5rem 2rem;
  background: #000;
  font-weight: 500;
  transition: all 200ms ease;

  &:hover {
    background: linear-gradient(90deg, blue, purple);
    color: #fff;
  }
}
</style>