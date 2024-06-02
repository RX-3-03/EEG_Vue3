<template>
  <div class="Container">
    <TabbarContainer class="ToggleVisibility" footerText="可见性切换">
      <LabelButton footerText="详细参数">
        <template #icon>
          <SvgIcon name="show all" />
        </template>
      </LabelButton>
    </TabbarContainer>
  </div>
</template>
<script setup lang="ts">
import LabelButton from '@/views/meg/components/labelButton.vue'
import TabbarContainer from '@/views/meg/components/tabbarContainer.vue'
</script>

<style scoped lang="scss">
.Container {
  display: flex;
  flex-wrap: wrap;
  gap: 10px;
}
</style>
