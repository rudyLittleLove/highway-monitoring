<script setup lang="ts">
// import { usePermissionStore } from '@/store/modules/permission'
// import { useRouter } from 'vue-router'
// import { useRouter } from 'vue-router'
import LeftColumn from './LeftColumn.vue'
import CenterColumn from './CenterColumn.vue'
import RightColumn from './RightColumn.vue'
</script>

<template>
  <div class="cockpit-index columns">
    <LeftColumn />
    <CenterColumn />
    <RightColumn />
  </div>
</template>

<style lang="less" scoped>
.cockpit-index {
  height: 100%;
  padding: 30px 46px;

  &.columns {
    display: flex;
    justify-content: space-between;
  }

  :deep(.item-title) {
    height: 40px;
    padding-left: 60px;
    margin-left: -10px;
    letter-spacing: 2px;
    background-image: url('/src/assets/imgs/item_title_bg.png');
    background-repeat: no-repeat;
    background-size: 100% auto;
    span {
      font-weight: bold;
      font-size: 24px;
      line-height: 1;
      color: #fffffb;
      text-shadow: 0px 3px 0px #233444;
    }
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
