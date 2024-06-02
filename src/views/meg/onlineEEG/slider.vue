<template>
  <MySlider title="记录控制">
    <MyCard title="工作流控制">
      <div class="button-group">
        <LabelButton footerText="完成">
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
      <div class="checkbox-group">
        <MyCheckBox
          text="点击取消/完成后重启工作流程"
          font-size="13px"
          :disabled="true"
        />
        <MyCheckBox
          text="点击取消/完成后回看工作流"
          font-size="13px"
          :disabled="true"
        />
        <MyCheckBox text="点击取消/完成后重回工作流" font-size="13px" />
      </div>
    </MyCard>
    <MyCard title="EEG">
      <div class="button-group">
        <LabelButton footerText="记录">
          <template #icon>
            <SvgIcon name="record" />
          </template>
        </LabelButton>
        <LabelButton footerText="阻抗">
          <template #icon>
            <SvgIcon name="impedance" />
          </template>
        </LabelButton>
      </div>
    </MyCard>
    <MyCard title="标注">
      <label></label>
    </MyCard>
  </MySlider>
</template>
<script setup lang="ts">
import MyCard from '@/views/meg/components/myCard.vue'
import LabelButton from '@/views/meg/components/labelButton.vue'
import MySlider from '@/views/meg/components/mySlider.vue'
import MyCheckBox from '@/views/meg/components/myCheckBox.vue'
</script>

<style scoped lang="scss">
.button-group {
  display: flex;
  flex-direction: row;
  gap: 10px;
  justify-content: center;
}

.checkbox-group {
  position: relative;
  left: -10px;
  width: 110%;
  display: flex;
  flex-direction: column;
}
</style>
