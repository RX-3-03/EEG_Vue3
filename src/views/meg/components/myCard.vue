<template>
  <div class="my-card">
    <div class="card-header">
      <span :style="{ fontSize: titleFontSize + 'px' }">{{ title }}</span>
    </div>
    <div class="card-content">
      <slot></slot>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue'

export default defineComponent({
  name: 'MyCard',
  props: {
    title: {
      type: String,
      default: 'Card Title',
    },
    titleFontSize: {
      type: Number,
      default: 13,
    },
  },
})
</script>

<style scoped>
.my-card {
  width: 100%;
  display: flex;
  flex-direction: column;
  /* 定义边框的圆角大小 */
  border-radius: 4px;
  padding: 0px;
  .card-header {
    padding: 5px;
    width: 100%;
    flex: 1;
    height: fit-content;
    background: #f5f4f1;
    font-weight: bold;
    border-radius: 2px;
  }
  .card-content {
    padding: 20px;
    display: flex;
    flex-direction: column;
    height: fit-content;
    width: 100%;
    justify-content: center;
    min-height: 10px; /* 确保内容高度至少为100px */
    gap: 3px;
    background: linear-gradient(to bottom, #c1e6fb, #8dc3e8);
    border-radius: 4px;
  }
}
</style>
