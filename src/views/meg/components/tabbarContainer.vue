<template>
  <div class="tabbarContainer">
    <div class="content">
      <slot></slot>
    </div>
    <div class="footer">
      {{ footerText }}
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent } from 'vue'

export default defineComponent({
  name: 'TabbarContainer',
  props: {
    footerText: {
      type: String,
      default: '',
    },
  },
})
</script>

<style scoped lang="scss">
.tabbarContainer {
  display: flex;
  flex-direction: column;
  border: 1px solid #ccc;
  border-radius: 10px;
  width: fit-content;
  .content {
    height: 100%;
    width: 100%;
    display: flex;
    justify-content: center;
    align-items: center;
    flex-direction: row;
    //column-count: 1; /* 初始列数 */
    //column-gap: 0; /* 列间距 */
    background: #e1f3fd;
    border-radius: 10px 10px 0 0;
  }

  .footer {
    height: fit-content;
    padding: 2px;
    font-size: 10px;
    text-align: center;
    border-radius: 1px 1px 10px 10px;
    background-color: #9ccdee;
    border-top: 1px solid #eee;
  }
}
</style>
