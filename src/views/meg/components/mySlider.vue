<template>
  <div class="container">
    <div class="slider-header">
      <span :style="{ fontSize: titleFontSize + 'px' }">{{ title }}</span>
    </div>
    <div class="slider-content">
      <slot></slot>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue'

export default defineComponent({
  name: 'MySlider',
  props: {
    title: {
      type: String,
      default: 'Card Title',
    },
    titleFontSize: {
      type: Number,
      default: 16,
    },
  },
})
</script>

<style scoped lang="scss">
.container {
  width: 100%;
  top: 5px;
  height: calc(100vh - $meg-tabbar-height - $meg-menu-height - 5px);
  display: flex;
  flex-wrap: wrap;
  border-radius: 4px;
  padding: 10px;
  flex-direction: column;
  background: #c1e6fb;
  gap: 10px;
  .slider-header {
    display: flex;
    flex-wrap: wrap;
    justify-content: space-between;
    padding: 8px;
    gap: 5px;
    font-weight: bold;
    background: linear-gradient(to right, #8bc2e7, #c1e6fb);
    height: fit-content;
    border-radius: 4px;
  }
  .slider-content {
    min-height: fit-content;
    display: flex;
    flex-direction: column;
    gap: 10px;
  }
}
</style>
