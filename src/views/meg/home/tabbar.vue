<template>
  <div class="container">
    <TabbarContainer class="EEGWorkFlows" footerText="EEG WorkFlows" :containerWidth="138">
      <LabelButton footerText="Acquire">
        <template #icon>
          <SvgIcon name="acquire" />
        </template>
      </LabelButton>
      <LabelButton footerText="Review & Export">
        <template #icon>
          <SvgIcon name="review" />
        </template>
      </LabelButton>
    </TabbarContainer>
    <TabbarContainer class="EEGWorkFlows" footerText="EEG WorkFlows" :containerWidth="280">
      <LabelButton footerText="Subject & Recording">
        <template #icon>
          <SvgIcon name="subject" />
        </template>
      </LabelButton>
      <LabelButton footerText="Edit Montage">
        <template #icon>
          <SvgIcon name="montage" />
        </template>
      </LabelButton>
      <LabelButton footerText="Edit Amplifier" @click="goEditAmplifier">
        <template #icon>
          <SvgIcon name="Amplifier" />
        </template>
      </LabelButton>
      <LabelButton footerText="Edit Annotations">
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

let $router = new useRouter()
const goEditAmplifier = (vc: any) => {
  $router.push('/meg/editAmplifier')
}
</script>

<style scoped lang="scss">
.container {
  display: flex;
  flex-wrap: wrap;
  gap: 10px;
}
</style>
