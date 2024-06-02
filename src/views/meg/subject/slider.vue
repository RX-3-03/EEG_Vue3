<template>
  <MySlider class="contatiner" title="回放和导出文件">
    <MyCard title="工作流控制">
      <div class="button-group">
        <LabelButton footerText="下一个">
          <template #icon>
            <SvgIcon name="finalize" />
          </template>
        </LabelButton>
        <LabelButton footerText="导出" @click="exportRecording">
          <template #icon>
            <SvgIcon name="export" />
          </template>
        </LabelButton>
        <el-dialog
          v-model="dialogFormVisible"
          title="导出选中数据"
          width="700"
          style="
            background-color: #c1e6fb;
            border-radius: 10px;
            padding: 20px;
            width: 500px;
            height: 350px;
            z-index: 9999;
          "
        >
          <div style="display: flex; flex-direction: column">
            <MyCheckBox text="应用后处理" font-size="13px" />
            <div style="padding: 0 0 0 20px">
              <div class="check-input">
                <MyCheckBox text="干电极后处理" font-size="13px" />
                <MyInput style="margin: 5px" label-width="300" />
              </div>
              <div class="check-input">
                <MyCheckBox text="启用模板和滤波器" font-size="13px" />
                <MyInput style="margin: 5px" label-width="280" />
              </div>
            </div>
            <MyCheckBox text="其他形式导出" font-size="13px" />
            <div style="padding: 0 0 0 20px">
              <div class="check-input">
                <MyCheckBox text="导出视频" font-size="13px" />
                <MyInput style="margin: 5px" label-width="300" />
              </div>
              <div class="check-input">
                <MyCheckBox text="导出SpO2传感器数据" font-size="13px" />
                <MyInput style="margin: 5px" label-width="270" />
              </div>
              <MySelectBox
                :options="options4"
                allow-clear
                style="align-items: center; padding: 10px"
                :width="420"
                v-model="selectedValue4"
                @change="onChange"
              />
            </div>
          </div>

          <div style="position: absolute; bottom: 20px; right: 30px">
            <OptionButton text="确认" />
            <OptionButton text="取消" />
          </div>
        </el-dialog>
      </div>
      <LabelButton footerText="取消">
        <template #icon>
          <SvgIcon name="cancel" />
        </template>
      </LabelButton>
    </MyCard>
    <MyCard title="选择">
      <div>
        <h2 style="font-size: small; margin-left: 14px;">Subject</h2>
        <!-- <label style="background-color: gray; font-size: small">
          Subject, Example, 1972-12-23
        </label> -->
        <MyInput label-width="160" style="margin-left: 12px"></MyInput>
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
        <h2 style="font-size: small; margin-bottom: 3px">Sampling Rate[Hz]</h2>
        <MySelectBox
          :options="options1"
          allow-clear
          :width="180"
          v-model="selectedValue1"
          @change="onChange"
        />
      </div>
      <div style="margin-bottom: 5px">
        <h2 style="font-size: small; margin-bottom: 3px">Amplifier Setup</h2>
        <MySelectBox
          :options="options2"
          allow-clear
          :width="180"
          v-model="selectedValue2"
          @change="onChange"
        />
      </div>
      <div>
        <h2 style="font-size: small; margin-bottom: 3px">Montage Setup</h2>
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
      <MyCheckBox text="启用SpO2传感器" font-size="13px" />
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
import OptionButton from '@/views/meg/components/applicationOption/optionButton.vue'
import MyInput from '@/views/meg/components/myInput.vue'

const dialogFormVisible = ref(false)
const exportRecording = () => {
  dialogFormVisible.value = true
}

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
const options4 = ref([
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
const selectedValue1 = ref('5')
const selectedValue2 = ref('5')
const selectedValue3 = ref('5')
const selectedValue4 = ref('5')

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
.check-input {
  display: flex;
  justify-content: space-between;
}
</style>
