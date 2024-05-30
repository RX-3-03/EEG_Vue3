<template>
  <MySlider class="contatiner" title="编辑放大器">
    <MyCard title="工作流控制">
      <LabelButton footerText="完成">
        <template #icon>
          <SvgIcon name="finalize" />
        </template>
      </LabelButton>
    </MyCard>
    <MyCard title="Amplifier Setup">
      <div  class="button-group">
        <LabelButton footerText="新建">
          <template #icon>
            <SvgIcon name="new" />
          </template>
        </LabelButton>
        <LabelButton footerText="删除">
          <template #icon>
            <SvgIcon name="delete" />
          </template>
        </LabelButton>
      </div>
      
    </MyCard>
    <MyCard title="Edit Selected Amplifier">
      <LabelButton footerText="Edit Amplifier">
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
</script>

<style scoped lang="scss">
.contatiner {
  display: flex;
  flex-wrap: wrap;
  flex-direction: column;
  gap: 10px;
}
.button-group{
  display: flex;
  flex-direction: row;
  gap: 10px;
  justify-content: center;
}
</style>
