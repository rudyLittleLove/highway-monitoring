<script setup lang="ts">
// import { usePermissionStore } from '@/store/modules/permission'
// import { useRouter } from 'vue-router'
import ToolHeader from '@/layout/components/ToolHeader.vue'
// import Index from '@/views/Cockpit/Index.vue'
// const { push } = useRouter()

// const permissionStore = usePermissionStore()
</script>

<template>
  <div class="cockpit-home">
    <div class="cockpit-header">
      <div class="cockpit-header-content flex items-center justify-between">
        <img src="/src/assets/imgs/icon_title.png" alt="" class="h-45px ml-17px" />
        <div class="cockpit-menu">
          <ul>
            <li>首页</li>
            <li>综合态势</li>
            <li>交通事件</li>
            <li>系统设置</li>
          </ul>
        </div>
        <ToolHeader />
      </div>
    </div>
    <div class="cockpit-body">
      <router-view />
    </div>
  </div>
</template>

<style lang="less" scoped>
.cockpit-home {
  height: 100%;
  background-image: url('/src/assets/imgs/screen_bg.png');
  background-size: cover;

  .cockpit-header {
    height: 137px;
    background-image: url('/src/assets/imgs/banner_bg.png');
    background-size: 100% auto;

    .cockpit-menu {
      width: calc(100% - 560px);
      height: 40px;

      ul {
        height: 100%;
      }

      li {
        float: left;
        width: 142px;
        height: 100%;
        padding-top: 5px;
        font-style: italic;
        color: #9bb5db;
        text-align: center;
        cursor: pointer;

        & + li {
          margin-left: -28px;
        }

        &.active,
        &:hover {
          color: #c6f9ff;
          background-image: url('/src/assets/imgs/menu_bg.png');
          background-size: auto 100%;
        }
      }
    }
  }

  .cockpit-body {
    height: calc(100% - 50px);
    margin-top: -87px;
  }
}
</style>
