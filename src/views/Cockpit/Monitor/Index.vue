<script setup lang="ts">
import { ref } from 'vue'
// import { usePermissionStore } from '@/store/modules/permission'
// import { useRouter } from 'vue-router'
import LeftColumn from './LeftColumn.vue'
import MonitorCard from './MonitorCard.vue'
import { hubMap } from '@/views/Cockpit/CONSTANT'
const active = ref<string>('全部枢纽')
</script>

<template>
  <div class="cockpit-monitor columns">
    <LeftColumn />
    <div class="center-column">
      <div class="menu-header">
        <ul>
          <li v-for="(item, i) in hubMap" :key="i" :class="{ active: active === item }">
            {{ item }}
          </li>
        </ul>
      </div>
      <div class="content-wrap">
        <MonitorCard placement="left-top" />
        <MonitorCard placement="right-top" />
        <MonitorCard placement="left-bottom" />
        <MonitorCard placement="right-bottom" />
      </div>
    </div>
  </div>
</template>

<style lang="less" scoped>
.cockpit-monitor {
  height: 100%;
  padding: 30px 46px;

  &.columns {
    display: flex;
    justify-content: space-between;
    .center-column {
      width: calc(100% - 532px);
      padding-left: 20px;
      .menu-header {
        height: 85px;
        letter-spacing: 1px;
        font-size: 18px;
        color: #eff8ff;
        ul {
          display: flex;
          justify-content: right;
        }
        li {
          width: 176px;
          height: 48px;
          margin-bottom: 18px;
          background-image: url('/src/assets/imgs/menu_bg1.png');
          background-size: 100% 100%;
          padding-top: 15px;
          padding-left: 39px;
          margin-left: 20px;
          line-height: 1;
          cursor: pointer;
          &:hover,
          &.active {
            color: #ffffff;
            background-image: url('/src/assets/imgs/menu_bg1_active.png');
            text-shadow: 0px 2px 4px #5ac9ff;
          }
        }
      }
      .content-wrap {
        position: relative;
        height: calc(100% - 85px);
      }
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
