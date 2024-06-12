<template>
  <MySlider class="contatiner" title="编辑放大器">
    <MyCard title="工作流控制">
      <LabelButton footerText="完成" @click="goRoute">
        <template #icon>
          <SvgIcon name="finalize" />
        </template>
      </LabelButton>
    </MyCard>
    <MyCard title="放大器">
      <div class="button-group">
        <LabelButton footerText="新建" @click="createMontage">
          <template #icon>
            <SvgIcon name="new" />
          </template>
        </LabelButton>
        <el-dialog
          v-model="dialogFormVisible"
          title="新建放大器模板"
          width="700"
          style="
            background-color: #c1e6fb;
            border-radius: 10px;
            padding: 20px;
            width: 400px;
            height: 280px;
            z-index: 9999;
          "
        >
          <div
            style="
              display: flex;
              flex-direction: column;
              align-items: center;
              gap: 10px;
            "
          >
            <label style="font-weight: bold">建立放大器模板</label>
            <MySelectBox
              :options="options4"
              allow-clear
              style="align-items: center"
              :width="330"
              v-model="selectedValue4"
              @change="onChange"
            />
            <label style="font-weight: bold">放大器模板名称设置</label>
            <MyInput style="margin: 5px" label-width="330" />
          </div>

          <div style="position: absolute; bottom: 20px; right: 30px">
            <OptionButton text="确认" />
            <OptionButton text="取消" />
          </div>
        </el-dialog>
        <LabelButton footerText="删除">
          <template #icon>
            <SvgIcon name="delete" />
          </template>
        </LabelButton>
      </div>
    </MyCard>
    <MyCard title="编辑所选放大器">
      <LabelButton footerText="编辑放大器">
        <template #icon>
          <SvgIcon name="edit" />
        </template>
      </LabelButton>
    </MyCard>
  </MySlider>
</template>
<script setup lang="ts">
import MyCard from '@/views/meg/components/myCard.vue'
import LabelButton from '@/views/meg/components/labelButton.vue'
import MySlider from '@/views/meg/components/mySlider.vue'
import MyInput from '@/views/meg/components/myInput.vue'
import MySelectBox from '@/views/meg/components/MySelectBox.vue'
import OptionButton from '@/views/meg/components/applicationOption/optionButton.vue'
import { useRouter } from 'vue-router'
import  { ref } from 'vue'

const dialogFormVisible = ref(false)
const createMontage = () => {
  dialogFormVisible.value = true
}

let $router = useRouter()
const goRoute = () => {
  $router.push('/meg/editMontage')
}

const options4 = ref([
  {
    label: 'EEG64',
    value: '1',
  },
  {
    label: 'EEG128',
    value: '2',
  },
  {
    label: 'EEG256',
    value: '3',
  },
])
const selectedValue4 = ref('1')
const onChange = (val: string) => {
  console.log(val)
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
