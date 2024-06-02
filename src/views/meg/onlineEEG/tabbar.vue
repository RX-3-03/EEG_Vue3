<template>
  <!-- Display窗体 -->
  <TabbarContainer class="ToggleVisibility" footerText="显示">
    <div class="selectDiv">
      <MySelectBox
        :options="options1"
        allow-clear
        :width="180"
        v-model="selectedValue1"
        @change="onChange"
      />
      <h2 class="selectboxfooter1">模板</h2>
      <MySelectBox
        :options="options2"
        allow-clear
        :width="100"
        v-model="selectedValue2"
        @change="onChange"
      />
      <h2 class="selectboxfooter1">Scale[uV]</h2>
    </div>
    <LabelButton>
      <template #icon>
        <SvgIcon name="down" />
      </template>
    </LabelButton>
    <div class="selectDiv">
      <MySelectBox
        :options="options5"
        allow-clear
        :width="140"
        v-model="selectedValue5"
        @change="onChange"
      />
      <h2 class="selectboxfooter2">通道显示</h2>
      <MySelectBox
        :options="options6"
        allow-clear
        :width="140"
        v-model="selectedValue6"
        @change="onChange"
      />
      <h2 class="selectboxfooter2">显示时间跨度</h2>
    </div>
    <LabelButton footerText="移除DC">
      <template #icon>
        <SvgIcon name="Removal" />
      </template>
    </LabelButton>
    <LabelButton footerText="冻结视图">
      <template #icon>
        <SvgIcon name="snow" />
      </template>
    </LabelButton>
  </TabbarContainer>
  <!-- Channel Selection窗体 -->
  <TabbarContainer class="ImportExport" footerText="通道选择">
    <LabelButton footerText="取消全选">
      <template #icon>
        <SvgIcon name="list" />
      </template>
    </LabelButton>
    <LabelButton footerText="反选">
      <template #icon>
        <SvgIcon name="share-internal" />
      </template>
    </LabelButton>
    <LabelButton footerText="全选">
      <template #icon>
        <SvgIcon name="select-all" />
      </template>
    </LabelButton>
    <LabelButton footerText="隐藏选择">
      <template #icon>
        <SvgIcon name="hide" />
      </template>
    </LabelButton>
    <LabelButton footerText="放大选中区域">
      <template #icon>
        <SvgIcon name="zoom" />
      </template>
    </LabelButton>
  </TabbarContainer>
  <!-- filter窗体 -->
  <TabbarContainer class="ImportExport" footerText="过滤器">
    <LabelButton footerText="Notch 50Hz">
      <template #icon>
        <SvgIcon name="notch" />
      </template>
    </LabelButton>
    <div>
      <MySelectBox
        :options="options3"
        allow-clear
        v-model="selectedValue3"
        @change="onChange"
      />
      <h2 class="selectboxfooter2">Low Cutoff[Hz]</h2>
      <MySelectBox
        :options="options4"
        allow-clear
        v-model="selectedValue4"
        @change="onChange"
      />
      <h2 class="selectboxfooter2">High Cutoff[Hz]</h2>
    </div>
    <LabelButton>
      <template #icon>
        <SvgIcon name="down" />
      </template>
    </LabelButton>
  </TabbarContainer>
  <!-- Events窗体 -->
  <TabbarContainer class="ImportExport" footerText="事件">
    <LabelButton footerText="显示事件">
      <template #icon>
        <SvgIcon name="video-camera" />
      </template>
    </LabelButton>
  </TabbarContainer>
  <!-- Scroll窗体 -->
  <TabbarContainer class="ImportExport" footerText="滚动">
    <LabelButton footerText="向上">
      <template #icon>
        <SvgIcon name="up" />
      </template>
    </LabelButton>
    <LabelButton footerText="向下">
      <template #icon>
        <SvgIcon name="down" />
      </template>
    </LabelButton>
  </TabbarContainer>
  <!-- 蒙太奇窗体 -->
  <TabbarContainer class="ImportExport" footerText="模板">
    <LabelButton footerText="保存">
      <template #icon>
        <SvgIcon name="Save" />
      </template>
    </LabelButton>
    <LabelButton footerText="另存为">
      <template #icon>
        <SvgIcon name="Save As" />
      </template>
    </LabelButton>
    <LabelButton footerText="显示不活跃通道">
      <template #icon>
        <SvgIcon name="show_channnels" />
      </template>
    </LabelButton>
  </TabbarContainer>
</template>

<script setup lang="ts">
import LabelButton from '@/views/meg/components/labelButton.vue'
import SvgIcon from '@/components/SvgIcon/index.vue'
import TabbarContainer from '@/views/meg/components/tabbarContainer.vue'
import MySelectBox from '../components/MySelectBox.vue'
import { ref, watchEffect } from 'vue'
const options1 = ref([
  {
    label: 'EEG64',
    value: '1',
  },
  {
    label: 'EEG65',
    value: '2',
  },
  {
    label: 'EEG66',
    value: '3',
  },
  {
    label: 'EEG67',
    value: '4',
  },
  {
    label: 'EEG68',
    value: '5',
  },
])
const options2 = ref([
  {
    label: '70',
    value: '1',
  },
  {
    label: '75',
    value: '2',
  },
  {
    label: '80',
    value: '3',
  },
  {
    label: '85',
    value: '4',
  },
  {
    label: '90',
    value: '5',
  },
])
const options3 = ref([
  {
    label: '0.3',
    value: '1',
  },
  {
    label: '0.4',
    value: '2',
  },
  {
    label: '0.5',
    value: '3',
  },
  {
    label: '0.6',
    value: '4',
  },
  {
    label: '0.7',
    value: '5',
  },
])
const options4 = ref([
  {
    label: '30',
    value: '1',
  },
  {
    label: '35',
    value: '2',
  },
  {
    label: '40',
    value: '3',
  },
  {
    label: '45',
    value: '4',
  },
  {
    label: '50',
    value: '5',
  },
])
const options5 = ref([
  {
    label: '1',
    value: '1',
  },
  {
    label: '2',
    value: '2',
  },
  {
    label: '3',
    value: '3',
  },
  {
    label: '4',
    value: '4',
  },
  {
    label: '5',
    value: '5',
  },
])
const options6 = ref([
  {
    label: '10',
    value: '1',
  },
  {
    label: '20',
    value: '2',
  },
  {
    label: '30',
    value: '3',
  },
  {
    label: '40',
    value: '4',
  },
  {
    label: '50',
    value: '5',
  },
])

const selectedValue1 = ref('5')
const selectedValue2 = ref('5')
const selectedValue3 = ref('5')
const selectedValue4 = ref('5')
const selectedValue5 = ref('5')
const selectedValue6 = ref('5')
watchEffect(() => {
  console.log('selectedValue1:', selectedValue1.value)
  console.log('selectedValue2:', selectedValue2.value)
  console.log('selectedValue3:', selectedValue3.value)
  console.log('selectedValue4:', selectedValue4.value)
  console.log('selectedValue5:', selectedValue4.value)
  console.log('selectedValue6:', selectedValue4.value)
})
function onChange(value: string | number, label: string, index: number) {
  console.log('value:', value)
  console.log('label:', label)
  console.log('index:', index)
}
</script>

<style scoped lang="scss">
.selectboxfooter1 {
  font-size: 12px;
  margin-left: 30px;
}

.selectboxfooter2 {
  font-size: 12px;
  margin-left: 15px;
}
</style>
