<script setup lang="ts">
import { ref } from 'vue'
import { useRoute } from 'vue-router'
import Menu from './menu/index.vue'
import Tabber from './tabbar/index.vue'
import Main from './main/index.vue'
import Slider from './slider/index.vue'
import useUserStore from '@/store/modules/user.ts'
import LayoutIcon1 from './LayoutIcon/index1.vue'
import LayoutIcon2 from './LayoutIcon/index2.vue'
import RecordEEG from '@/views/meg/components/applicationOption/recordEEG.vue'
import MyTabs from '@/views/meg/components/myTabs.vue'
import MyTabPane from '@/views/meg/components/myTabPane.vue'
import Device from '@/views/meg/components/applicationOption/device.vue'
import OptionButton from '@/views/meg/components/applicationOption/optionButton.vue'
import useMegSettingStore from '@/store/modules/megSetting.ts'

let userStore = useUserStore()
let $route = useRoute()
const dialogFormVisible = ref(false)
const applicationOption = () => {
  dialogFormVisible.value = true
  // MegSettingStore.fold = !MegSettingStore.fold
}
useMegSettingStore().fold = true
let MegSettingStore = useMegSettingStore()

</script>

<template>
  <div class="layout_container">
    <div class="layout_menu">
      <button class="applicationOption" @click="applicationOption">设置</button>
      <el-dialog v-model="dialogFormVisible" title="应用设置" width="700" style="
          background-color: #c1e6fb;
          border-radius: 10px;
          padding: 20px;
          height: 600px;
          z-index: 9999;
        ">
        <MyTabs name="Record EEG" default="caa">
          <MyTabPane tab="概览" name="tab1">ccccc</MyTabPane>
          <MyTabPane tab="脑电测量" name="recordEEG">
            <RecordEEG />
          </MyTabPane>
          <MyTabPane tab="干脑电模型" name="dryModule">eeeee</MyTabPane>
          <MyTabPane tab="设备" name="device">
            <Device />
          </MyTabPane>
          <MyTabPane tab="标注" name="annotation">ccccc</MyTabPane>
          <MyTabPane tab="网络操作" name="Network">ccccc</MyTabPane>
        </MyTabs>
        <div style="position: absolute; bottom: 20px; right: 30px">
          <OptionButton text="确认" />
          <OptionButton text="取消" />
        </div>
      </el-dialog>
      <el-menu :default-active="$route.path" active-text-color="#fff" background-color="#001529" text-color="#959ea6"
        mode="horizontal">
        <Menu :menuList="userStore.menuRoutes[2].children" />
      </el-menu>
    </div>
    <div class="layout_tabbar">
      <Tabber />
    </div>
    <div class="layout_icon1">
      <LayoutIcon1 />
    </div>
    <div class="layout_slider" :class="{ fold: MegSettingStore.fold ? true : false }">
      <Slider />
    </div>
    <div class="layout_icon2">
      <LayoutIcon2 />
    </div>
    <div class="layout_main" :class="{ fold: MegSettingStore.fold ? true : false }">
      <Main />
    </div>
    <!-- <div class="layout_footer"></div> -->
  </div>
</template>

<style lang="scss" scoped>
.layout_container {
  width: 100vw;
  height: 100vh;
  // background: linear-gradient(to center, #8bc2e7, #c1e6fb);
  background: #c1e6fb;

  .layout_menu {
    height: $meg-menu-height;
    width: 100vw;
    background: #81a2be;
    display: flex;

    .el-button {
      height: $meg-menu-height;
    }

    .el-menu {
      flex: 1;
      height: $meg-menu-height;
    }
  }

  .layout_tabbar {
    position: fixed;
    top: $meg-menu-height;
    width: 100vw;
    height: $meg-tabbar-height;
    z-index: 100;
    display: flex;
    flex-direction: row;
    padding: 3px;
    gap: 8px;
  }

  .layout_footer {
    position: fixed;
    bottom: 0;
    width: 100vw;
    height: 20px;
    background-color: white;
    border-top: 1px solid black;
  }

  .layout_icon1 {
    position: fixed;
    top: calc($meg-menu-height + $meg-tabbar-height);
    left: 0;
    right: 0;
    width: 100vw;
    height: $meg-icon-height;
    background-color: #9ccdee;
  }

  .layout_slider {
    position: absolute;
    width: $meg-slider-width;
    top: calc($meg-menu-height + $meg-tabbar-height + $meg-icon-height);
    height: calc(100vh - $meg-menu-height - $meg-tabbar-height - $meg-icon-height );

    &.fold {
      width: 0;
    }
  }

  .layout_icon2 {
    position: fixed;
    top: calc($meg-menu-height + $meg-tabbar-height + $meg-icon-height);
    width: 20px;
    left: $meg-slider-width;
    bottom: 20px;
    height: calc(100vh - $meg-menu-height - $meg-tabbar-height - $meg-icon-height );
  }

  .layout_main {
    position: fixed;
    top: calc($meg-menu-height + $meg-tabbar-height + $meg-icon-height);
    left: calc($meg-slider-width + 20px);
    right: 0;
    bottom: 20px;
    width: calc(100vw - $meg-slider-width);
    height: calc(100vh - $meg-menu-height - $meg-tabbar-height - $meg-icon-height );

    &.fold {
      left: 0px;
      width: 100vw;
    }
  }
}
</style>
