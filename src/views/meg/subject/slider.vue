<template>
  <MySlider class="contatiner" title="记录EEG">
    <MyCard title="工作流控制 ">
      <div class="button-group">
        <LabelButton footerText="下一步">
          <template #icon>
            <SvgIcon name="finalize" />
          </template>
        </LabelButton>
        <LabelButton footerText="取消">
          <template #icon>
            <SvgIcon name="cancel" />
          </template>
        </LabelButton>
      </div>
    </MyCard>
    <MyCard title="选择记录">
      <div>
        <h2 style="font-size: small">Subject</h2>
        <label style="background-color: gray; font-size: small"> Subject, Example, 1972-12-23 </label>
      </div>
      <br />
      <div class="button-group">
        <LabelButton footerText="新建">
          <template #icon>
            <SvgIcon name="new" />
          </template>
        </LabelButton>
      </div>
    </MyCard>
    <MyCard title="记录参数">
      <div style="margin-bottom: 5px">
        <h2 style="font-size: small">Sampling Rate[Hz]</h2>
        <MySelectBox
          :options="options1"
          allow-clear
          :width="180"
          v-model="selectedValue1"
          @change="onChange"
        />
      </div>
      <div style="margin-bottom: 5px">
        <h2 style="font-size: small">Amplifier Setup</h2>
        <MySelectBox
          :options="options2"
          allow-clear
          :width="180"
          v-model="selectedValue2"
          @change="onChange"
        />
      </div>
      <div>
        <h2 style="font-size: small">Montage Setup</h2>
        <MySelectBox
          :options="options3"
          allow-clear
          :width="180"
          v-model="selectedValue3"
          @change="onChange"
        />
      </div>
    </MyCard>
    <MyCard title="传感器">
      <MyCheckBox text="使用SpO2传感器" font-size="13px" />
    </MyCard>
  </MySlider>
</template>
<script setup lang="ts">
import MyCard from '@/views/meg/components/myCard.vue'
import LabelButton from '@/views/meg/components/labelButton.vue'
import MySlider from '@/views/meg/components/mySlider.vue'
import MySelectBox from '../components/MySelectBox.vue'
import MyCheckBox from '@/views/meg/components/myCheckBox.vue'
import { ref, watchEffect } from 'vue'

const options1 = ref([
  {
    label: '200',
    value: '1',
  },
  {
    label: '300',
    value: '2',
  },
  {
    label: '400',
    value: '3',
  },
  {
    label: '500',
    value: '4',
  },
  {
    label: '600',
    value: '5',
  },
])
const options2 = ref([
  {
    label: 'EEG64-AUX-CA-208',
    value: '1',
  },
  {
    label: 'EEG65-CA-208',
    value: '2',
  },
  {
    label: 'EEG66-CA-208',
    value: '3',
  },
  {
    label: 'EEG67-CA-208',
    value: '4',
  },
  {
    label: 'EEG68-CA-208',
    value: '5',
  },
])
const options3 = ref([
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

const selectedValue1 = ref('5')
const selectedValue2 = ref('5')
const selectedValue3 = ref('5')

watchEffect(() => {
  console.log('selectedValue1:', selectedValue1.value)
  console.log('selectedValue2:', selectedValue2.value)
  console.log('selectedValue3:', selectedValue3.value)
})

function onChange(value: string | number, label: string, index: number) {
  console.log('value:', value)
  console.log('label:', label)
  console.log('index:', index)
}
</script>

<style scoped lang="scss">
.contatiner {
  display: flex;
  flex-wrap: wrap;
  flex-direction: column;
  gap: 10px;
}

.button-group {
  display: flex;
  flex-direction: row;
  gap: 10px;
  justify-content: center;
}
</style>
