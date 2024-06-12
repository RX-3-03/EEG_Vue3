<template>
  <div class="container">
    <TabbarContainer
      class="EEGWorkFlows"
      footerText="EEG工作流"
      :containerWidth="138"
    >
      <LabelButton footerText="导入">
        <template #icon>
          <SvgIcon name="acquire" />
        </template>
      </LabelButton>
      <LabelButton footerText="回放 & 导出">
        <template #icon>
          <SvgIcon name="review" />
        </template>
      </LabelButton>
    </TabbarContainer>
    <TabbarContainer
      class="EEGWorkFlows"
      footerText="管理工作流"
      :containerWidth="280"
    >
      <LabelButton footerText="主题 & 记录">
        <template #icon>
          <SvgIcon name="subject" />
        </template>
      </LabelButton>
      <LabelButton footerText="编辑模板">
        <template #icon>
          <SvgIcon name="montage" />
        </template>
      </LabelButton>
      <LabelButton footerText="编辑放大器" @click="goEditAmplifier">
        <template #icon>
          <SvgIcon name="Amplifier" />
        </template>
      </LabelButton>
      <LabelButton footerText="编辑标签">
        <template #icon>
          <SvgIcon name="annotations" />
        </template>
      </LabelButton>
    </TabbarContainer>
  </div>
</template>
<script setup lang="ts">
import MyButton from '@/views/meg/components/myButton.vue'
import TabbarContainer from '@/views/meg/components/tabbarContainer.vue'
import LabelButton from '@/views/meg/components/labelButton.vue'
import { useRouter } from 'vue-router'
import useMegSettingStore from '@/store/modules/megSetting'

let $router = new useRouter()
const goEditAmplifier = (vc: any) => {
  $router.push('/meg/editAmplifier')
  useMegSettingStore().fold = false
}
</script>

<style scoped lang="scss">
.container {
  display: flex;
  flex-wrap: wrap;
  gap: 10px;
}
</style>
