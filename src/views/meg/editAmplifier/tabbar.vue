<template>
  <div class="Container">
    <TabbarContainer
      class="ToggleVisibility"
      footerText="切换可见性"
      :containerWidth="85"
    >
      <LabelButton footerText="显示全部">
        <template #icon>
          <SvgIcon name="show all" />
        </template>
      </LabelButton>
    </TabbarContainer>
    <TabbarContainer
      class="ImportExport"
      footerText="导入 & 导出"
      :containerWidth="138"
    >
      <LabelButton footerText="导入文件">
        <template #icon>
          <SvgIcon name="import" />
        </template>
      </LabelButton>
      <LabelButton footerText="导出文件">
        <template #icon>
          <SvgIcon name="export" />
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
