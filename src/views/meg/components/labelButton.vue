<template>
  <div class="labelbutton-btn-container">
    <button class="labelbutton-btn">
      <slot name="icon"></slot>
    </button>
    <div class="labelbutton-footer">
      {{ footerText }}
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue'

export default defineComponent({
  name: 'labelButton',
  props: {
    footerText: {
      type: String,
      default: '',
    },
  },
})
</script>

<style scoped lang="scss">
.labelbutton-btn-container {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 5px;
}
.labelbutton-btn {
  width: calc($meg-buttom-size * 1);
  height: calc($meg-buttom-size * 1);
  display: inline-block;
  background: #e3edf7;
  border-radius: 10px;
  cursor: pointer;
  transition: transform 0.5s;
  writing-mode: horizontal-tb;
  border: 1px solid rgba(0, 0, 0, 0.1);
}

.labelbutton-btn:hover {
  box-shadow: inset 4px 4px 6px -1px rgba(0, 0, 0, 0.2),
    inset -4px -4px 6px -1px rgba(255, 255, 255, 0.7),
    -0.5px -0.5px 0px rgba(255, 255, 255, 1),
    0.5px 0.5px 0px rgba(0, 0, 0, 0.15), 0px 12px 10px -10px rgba(0, 0, 0, 0.05);
  border: 1px solid rgba(0, 0, 0, 0.1);
}

.labelbutton-btn:hover svg {
  transform: scale(0.9);
  fill: #333333;
}

.labelbutton-footer {
  height: 14px;
  font-size: 11px;
  width: calc($meg-buttom-size * 1.5);
  text-align: center;
  white-space: normal;
}
</style>
