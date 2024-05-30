<script lang="ts">
import { defineComponent } from 'vue'

export default defineComponent({
  name: 'MyCheckBox',
  props: {
    text: {
      type: String,
      default: 'checkbox',
    },
    fontSize: {
      type: String,
      default: '14px',
    },
    disabled: {
      type: Boolean,
      default: false,
    },
  },
})
</script>

<template>
  <label class="material-checkbox">
    <input type="checkbox" :disabled="disabled" />
    <span class="checkmark" />
    <span :style="{ fontSize: fontSize }">{{ text }}</span>
  </label>
</template>

<style>
.material-checkbox {
  display: flex;
  align-items: center;
  font-size: 14px;
  cursor: pointer;
  margin: 5px;
}

.material-checkbox input[type='checkbox'] {
  position: absolute;
  opacity: 0;
  width: 0;
  height: 0;
}

.checkmark {
  position: relative;
  display: inline-block;
  width: 15px;
  height: 15px;
  margin-right: 8px;
  border: 2px solid white;
  border-radius: 4px;
  transition: all 0.3s;
  max-height: 15px;
  min-width: 15px;
}

.material-checkbox input[type='checkbox']:checked ~ .checkmark {
  background-color: #4da1db;
  border-color: #4da1db;
}

.material-checkbox input[type='checkbox']:checked ~ .checkmark:after {
  content: '';
  position: absolute;
  top: 0px;
  left: 4px;
  width: 4px;
  height: 10px;
  border: solid white;
  border-width: 0 2px 2px 0;
  transform: rotate(45deg);
}

.material-checkbox:hover input[type='checkbox'] ~ .checkmark {
  border-color: #4da1db;
}

.material-checkbox input[type='checkbox']:disabled ~ .checkmark {
  opacity: 0.5;
  cursor: not-allowed;
}

.material-checkbox input[type='checkbox']:disabled ~ .checkmark:hover {
  border-color: #4da1db;
}
</style>
