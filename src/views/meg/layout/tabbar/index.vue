<script setup lang="ts"></script>

<script lang="ts">
export default {
  name: 'Tabbar',
}
</script>

<template>
  <router-view name="tabberRouter" v-slot="{ Component }">
    <transition name="fade">
      <component :is="Component" />
    </transition>
  </router-view>
</template>

<style scoped lang="scss">
.tabberRouter {
  width: 100%;
  height: 100%;
}
</style>
