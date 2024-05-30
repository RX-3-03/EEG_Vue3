<template>
  <TabbarContainer
    class="ImportExport"
    footerText="输入和输出"
  >
    <LabelButton footerText="Import">
      <template #icon>
        <SvgIcon name="import" />
      </template>
    </LabelButton>
    <LabelButton footerText="Export">
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

<style scoped lang="scss">

</style>
