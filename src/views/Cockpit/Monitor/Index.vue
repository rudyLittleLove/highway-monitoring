<script setup lang="ts">
// import { usePermissionStore } from '@/store/modules/permission'
// import { useRouter } from 'vue-router'
import LeftColumn from './LeftColumn.vue'
</script>

<template>
  <div class="cockpit-monitor columns">
    <LeftColumn />
  </div>
</template>

<style lang="less" scoped>
.cockpit-monitor {
  height: 100%;
  padding: 30px 46px;

  &.columns {
    display: flex;
    justify-content: space-between;
  }

  :deep(.linear-text) {
    font-size: 14px;
    font-weight: bold;
    color: #ffffff;

    background-image: -webkit-linear-gradient(top, #ffffff, #7df6ff);
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
  }
}
</style>
