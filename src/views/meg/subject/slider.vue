<template>
  <MySlider class="contatiner" title="Edit Amplifier">
    <MyCard title="Workflow Control">
      <div class="button-group">
        <LabelButton footerText="Next">
          <template #icon>
            <SvgIcon name="finalize" />
          </template>
        </LabelButton>
        <LabelButton footerText="Cancel">
          <template #icon>
            <SvgIcon name="cancel" />
          </template>
        </LabelButton>
      </div>
    </MyCard>
    <MyCard title="Selection">
      <div class="button-group">
        <LabelButton footerText="New">
          <template #icon>
            <SvgIcon name="new" />
          </template>
        </LabelButton>
        <LabelButton footerText="Delete">
          <template #icon>
            <SvgIcon name="delete" />
          </template>
        </LabelButton>
      </div>
    </MyCard>
    <MyCard title="Recording Parameters">
      <div>
        <h2 class="selectboxfooter1">Sampling Rate[Hz]</h2>
        <MySelectBox :options="options1" allow-clear :width="180" v-model="selectedValue1" @change="onChange" />
      </div>
      <div>
        <h2 class="selectboxfooter1">Amplifier Setup</h2>
        <MySelectBox :options="options2" allow-clear :width="180" v-model="selectedValue1" @change="onChange" />
      </div>
      <div>
        <h2 class="selectboxfooter1">Montage Setup</h2>
        <MySelectBox :options="options3" allow-clear :width="180" v-model="selectedValue1" @change="onChange" />
      </div>
    </MyCard>
    <MyCard title="Sensors"></MyCard>
  </MySlider>
</template>
<script setup lang="ts">
import MyCard from '@/views/meg/components/myCard.vue'
import LabelButton from '@/views/meg/components/labelButton.vue'
import MySlider from '@/views/meg/components/mySlider.vue'
import MySelectBox from '../components/MySelectBox.vue'
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
