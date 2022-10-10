<script setup lang="ts">
import { ref } from 'vue'
import PointHub from './Point.vue'
import { hubMap } from '@/views/Cockpit/CONSTANT'

const active = ref<string>('全部枢纽')
</script>

<template>
  <div class="center-column">
    <div class="left-menu">
      <ul>
        <li v-for="(item, i) in hubMap" :key="i" :class="{ active: active === item }">
          {{ item }}
        </li>
      </ul>
    </div>
    <PointHub left="900px" top="72px" :number="1" :name="hubMap[1]" />
    <PointHub left="857px" top="210px" :number="2" :name="hubMap[2]" />
    <PointHub left="766px" top="250px" :number="3" :name="hubMap[3]" />
    <PointHub left="590px" top="353px" :number="4" :name="hubMap[4]" />
    <PointHub left="390px" top="666px" :number="5" :name="hubMap[5]" />
  </div>
</template>

<style lang="less" scoped>
.center-column {
  width: calc(100% - 1064px);
  padding: 0 24px;
  position: relative;
  background-image: url('/src/assets/imgs/path_bg.png');
  background-size: 100% auto;
  background-repeat: no-repeat;
  .left-menu {
    position: absolute;
    top: 0;
    left: 24px;
    color: #eff8ff;
    letter-spacing: 1px;
    font-size: 18px;

    li {
      width: 176px;
      height: 48px;
      margin-bottom: 18px;
      background-image: url('/src/assets/imgs/menu_bg1.png');
      background-size: 100% 100%;
      padding-top: 15px;
      padding-left: 39px;
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
}
</style>
