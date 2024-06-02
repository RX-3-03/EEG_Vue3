<template>
  <TabbarContainer class="ImportExport" footerText="导入&导出">
    <LabelButton footerText="导入">
      <template #icon>
        <SvgIcon name="import" />
      </template>
    </LabelButton>
    <LabelButton footerText="导出">
      <template #icon>
        <SvgIcon name="export" />
      </template>
    </LabelButton>
  </TabbarContainer>
</template>
<script setup lang="ts">
import LabelButton from '@/views/meg/components/labelButton.vue'
import TabbarContainer from '@/views/meg/components/tabbarContainer.vue'
</script>

<style scoped lang="scss"></style>
