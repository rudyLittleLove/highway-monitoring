<script setup lang="ts">
// import { usePermissionStore } from '@/store/modules/permission'
// import { useRouter } from 'vue-router'
import LeftColumn from './LeftColumn.vue'
import RightColumn from './RightColumn.vue'
</script>

<template>
  <div class="cockpit-index columns">
    <LeftColumn />
    <RightColumn />
  </div>
</template>

<style lang="less" scoped>
.cockpit-index {
  height: 100%;
  padding: 20px 30px;

  &.columns {
    display: flex;
    justify-content: space-between;
  }

  :deep(.item-title) {
    height: 35px;
    padding-left: 40px;
    margin-left: -10px;
    font-style: italic;
    font-weight: bold;
    letter-spacing: 2px;
    color: #fffffb;
    text-shadow: 2px 2px 1px #000000;
    background-image: url('/src/assets/imgs/item_title_bg.png');
    background-repeat: no-repeat;
    background-size: 100% auto;
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
