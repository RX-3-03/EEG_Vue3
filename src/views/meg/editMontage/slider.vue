<template>
  <MySlider title="采集模板设置">
    <MyCard title="工作流控制">
      <LabelButton footerText="Finalize">
        <template #icon>
          <SvgIcon name="finalize" />
        </template>
      </LabelButton>
    </MyCard>
    <MyCard title="新建模板">
      <div class="button-group">
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
    <MyCard title="编辑选中模板">
      <LabelButton footerText="编辑模板">
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
.button-group{
  display: flex;
  flex-direction: row;
  gap: 10px;
  justify-content: center;
}
</style>
