<script setup lang="ts"></script>

<template>
  <div class="left-column">
    <div class="item-title">
      <span>实时监控</span>
    </div>
    <div class="card-box" v-for="i in 4" :key="i">
      <div class="header">
        <span class="text">Camera 01 隰县北互通上行方向 出口</span>
        <span> <img src="/src/assets/imgs/scale_icon.png" class="scale-icon" alt="" /> </span>
      </div>
      <div class="view-box"></div>
    </div>
  </div>
</template>

<style lang="less" scoped>
.left-column {
  width: 532px;
  padding: 20px 34px;
  background-image: url('/src/assets/imgs/L.png');
  background-size: 100% 100%;

  .card-box {
    margin-top: 14px;
    margin-bottom: 14px;
    .header {
      height: 30px;
      background-image: url('/src/assets/imgs/item_title_blu_bg.png'),
        linear-gradient(-90deg, rgba(0, 48, 103, 0.21), rgba(0, 36, 67, 0.92));
      background-size: auto 100%;
      background-repeat: no-repeat;
      padding-top: 3px;
      position: relative;

      .scale-icon {
        width: 12px;
        height: 12px;
        cursor: pointer;
        margin: 6px 9px 0 0;
        float: right;
      }
      .text {
        font-size: 14px;
        letter-spacing: 1px;
        box-shadow: none;
        padding-left: 35px;

        background: linear-gradient(180deg, #ffffff 0%, #4eb3ff 100%);
        -webkit-background-clip: text;
        -webkit-text-fill-color: transparent;
      }
      span:nth-of-type(2) {
        float: right;
      }
    }
    .view-box {
      margin-top: -30px;
      height: 208px;
      background-color: #ffffff;
    }
  }
}
</style>
