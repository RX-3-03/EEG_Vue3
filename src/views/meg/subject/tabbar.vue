<template>
  <div class="Container">
    <TabbarContainer class="ToggleVisibility" footerText="Toggle Visibility" :containerWidth="85">
      <LabelButton footerText="Detailed Parameters">
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
