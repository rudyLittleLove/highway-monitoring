<script setup lang="ts">
import { ref, onUnmounted } from 'vue'
import ToolHeader from '@/layout/components/ToolHeader.vue'
import dayjs from 'dayjs'
import { ElDivider } from 'element-plus'

const time = ref<string>('')
const week = ref<string>('')
const yearToDate = ref<string>('')
var timer: any = ''
// 自动更新时间
const getNewDate: () => void = () => {
  let date = new Date()

  time.value = dayjs(date).format('HH:mm:ss')

  week.value = dayjs(date).format('ddd')

  yearToDate.value = dayjs(date).format('YYYY/MM/DD')
  timer = setTimeout(() => {
    getNewDate()
  }, 1000)
}
getNewDate()

// 自适应页面
const scaleStyle = ref<string>('')
const calcScale: () => void = () => {
  console.log(1)
  let winW = window.innerWidth

  let scale = winW / 2560
  scaleStyle.value = `transform: scale(${scale},${scale});`
}
calcScale()
window.addEventListener('resize', calcScale)

onUnmounted(() => {
  window.removeEventListener('resize', calcScale)
  clearTimeout(timer)
})
</script>

<template>
  <div class="cockpit-home" :style="scaleStyle">
    <div class="cockpit-header">
      <div class="cockpit-header-content flex items-center justify-between">
        <img src="/src/assets/imgs/icon_title.png" alt="" class="h-58px ml-46px mt-10px" />
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
  width: 2560px;
  height: 1080px;
  position: fixed;
  left: 0;
  top: 0;
  transform-origin: 0 0;
  background-image: url('/src/assets/imgs/screen_bg.png');
  background-size: 100% 100%;

  @font-face {
    font-family: 'JiangChengXieHei-500W';
    src: url('/src/assets/font/jiangchengxiehei.ttf') format('truetype');
  }
  @font-face {
    font-family: 'D-DIN';
    src: url('/src/assets/font/D-Din/D-DIN.ttf') format('truetype');
  }
  @font-face {
    font-family: 'pangmen';
    src: url('/src/assets/font/pangmengzhengdaobiaoti.ttf') format('truetype');
  }

  font-family: JiangChengXieHei-500W;

  .cockpit-header {
    height: 182px;
    background-image: url('/src/assets/imgs/banner_bg.png');
    background-size: 100% 100%;
    .cockpit-header-content {
      height: 60px;
    }

    .cockpit-menu {
      width: 1650px;
      height: 60px;

      ul {
        height: 100%;
      }

      li {
        float: left;
        width: 220px;
        height: 100%;
        padding-top: 20px;
        line-height: 1;
        color: #9bb5db;
        text-align: center;
        cursor: pointer;
        font-size: 22px;

        & + li {
          margin-left: -50px;
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
      padding-right: 20px;
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
        // margin-top: 3px;
        transform: translateY(5px);
        margin-right: 5px;
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
    height: calc(100% - 60px);
    margin-top: -122px;
  }
}
</style>
