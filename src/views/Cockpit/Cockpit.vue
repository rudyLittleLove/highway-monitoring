<script setup lang="ts">
import { ref } from 'vue'
import ToolHeader from '@/layout/components/ToolHeader.vue'
import dayjs from 'dayjs'
import { ElDivider } from 'element-plus'

const time = ref<string>('')
const week = ref<string>('')
const yearToDate = ref<string>('')

const getNewDate: () => void = () => {
  let date = new Date()

  time.value = dayjs(date).format('HH:mm:ss')

  week.value = dayjs(date).format('ddd')

  yearToDate.value = dayjs(date).format('YYYY/MM/DD')
  setTimeout(() => {
    getNewDate()
  }, 1000)
}
getNewDate()
</script>

<template>
  <div class="cockpit-home">
    <div class="cockpit-header">
      <div class="cockpit-header-content flex items-center justify-between">
        <img src="/src/assets/imgs/icon_title.png" alt="" class="h-45px ml-17px" />
        <div class="cockpit-menu">
          <ul>
            <li class="active">首页</li>
            <li>综合态势</li>
            <li>交通事件</li>
            <li>系统设置</li>
          </ul>
        </div>
        <div class="top-right">
          <div class="row">
            <div class="time">{{ time }}</div>
            <div class="date">
              <div class="week">{{ week }}</div>
              <div class="yearToDate">{{ yearToDate }}</div>
            </div>
            <ElDivider direction="vertical" />
            <ToolHeader />
          </div>
          <div class="line"> <span></span><span></span><span></span> </div>
        </div>
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
      width: calc(100% - 700px);
      height: 40px;

      ul {
        height: 100%;
      }

      li {
        float: left;
        width: 142px;
        height: 100%;
        padding-top: 7px;
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
    .top-right {
      .row {
        display: flex;
        color: #ffffff;
        .time {
          font-size: 22px;
          line-height: 0.9;
        }
        .yearToDate,
        .week {
          line-height: 1;
          font-size: 12px;
          transform-origin: top;
          transform: scale(0.8);
        }
      }
      .line {
        height: 1px;
        background-color: #1bd0fe;
        margin-top: 3px;
        margin-right: 10px;
        span {
          float: left;
          width: 6px;
          height: 6px;
          border-radius: 3px;
          border: 1px solid #ffffff;
          background-color: #04203c;
          margin-top: -3px;
          &:nth-of-type(2) {
            margin-left: 153px;
          }
          &:nth-of-type(3) {
            float: right;
          }
        }
      }
      .el-divider {
        height: 20px;
        border-left-color: #979797;
      }
      .v-tool-header {
        height: auto;
        margin-top: -3px;
      }
    }
  }

  .cockpit-body {
    height: calc(100% - 50px);
    margin-top: -87px;
  }
}
</style>
