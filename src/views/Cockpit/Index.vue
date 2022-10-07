<script setup lang="ts">
// import { usePermissionStore } from '@/store/modules/permission'
// import { useRouter } from 'vue-router'
// import ToolHeader from '@/layout/components/ToolHeader.vue'
// const { push } = useRouter()

// const permissionStore = usePermissionStore()
const jamTop: any = [
  {
    label: 'Top1 隰县北互通 入口',
    value: '90m',
    ratio: '80%'
  },
  {
    label: 'Top2 大宁互通 出口',
    value: '82m',
    ratio: '70%'
  },
  {
    label: 'Top1 午成互通 出口',
    value: '76m',
    ratio: '60%'
  },
  {
    label: 'Top1 窑头互通 入口',
    value: '68m',
    ratio: '50%'
  },
  {
    label: 'Top1 寨子枢互通 出口',
    value: '56m',
    ratio: '40%'
  }
]
</script>

<template>
  <div class="cockpit-index columns">
    <div class="left-column">
      <div class="item-title">数据统计</div>
      <div class="data-statistics">
        <div class="column">
          <img src="@/assets/imgs/accident_icon.png" alt="" />
          <div class="column-info">
            <div class="title">累计拥堵时长</div>
            <div class="text">
              <span class="num linear-text">46分钟</span>
              <span class="ratio">3.9%</span>
            </div>
          </div>
        </div>
        <div class="column">
          <img src="@/assets/imgs/accident_icon.png" alt="" />
          <div class="column-info">
            <div class="title">今日事故报警</div>
            <div class="text">
              <span class="num linear-text">46起</span>
              <span class="ratio">3.9%</span>
            </div>
          </div>
        </div>
      </div>
      <div class="item-title">拥堵排行</div>
      <div class="jam-top">
        <ul>
          <li v-for="(item, i) in jamTop" :key="i">
            <div class="info-row">
              <span class="label">{{ item.label }}</span>
              <span class="linear-text">{{ item.value }}</span>
            </div>
            <div class="bar-row">
              <div class="bar" :style="`width: ${item.ratio}`"></div>
            </div>
          </li>
        </ul>
      </div>
      <div class="item-title">实时事件报警</div>
    </div>
  </div>
</template>

<style lang="less" scoped>
.cockpit-index {
  height: 100%;
  padding: 20px 30px;

  &.columns {
    display: flex;
  }

  .item-title {
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

  .linear-text {
    font-size: 14px;
    font-weight: bold;
    color: #ffffff;

    background-image: -webkit-linear-gradient(top, #ffffff, #7df6ff);
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
  }

  .left-column {
    width: 400px;
    padding: 20px 25px;
    background-image: url('/src/assets/imgs/L.png');
    background-size: 100% 100%;

    .data-statistics {
      display: flex;
      padding: 25px 0;
      justify-content: space-between;

      .column {
        display: flex;
        width: 45%;
        justify-content: space-between;

        > img {
          width: 75px;
          height: auto;
        }

        .column-info {
          padding-top: 15px;
        }

        .title {
          width: 100%;
          padding-left: 8px;
          font-size: 12px;
          color: #ffffff;
          background-image: linear-gradient(90deg, rgba(0, 145, 255, 1), rgba(0, 145, 255, 0));
          border-radius: 2px;
        }

        .ratio {
          padding-left: 5px;
          font-size: 12px;
          color: #ffffff;
        }
      }
    }

    .jam-top {
      padding: 25px 0;
      font-size: 12px;
      font-style: italic;

      li {
        height: 45px;

        .info-row {
          display: flex;
          justify-content: space-between;
          padding-right: 2px;

          .label {
            padding-left: 10px;
            color: #ffffff;
          }
        }

        .bar-row {
          height: 7px;
          margin-top: 2px;
          background-color: #274d6f;
          box-shadow: 0 0 2px rgba(0, 0, 0, 0.2);

          .bar {
            height: 100%;
            background-image: linear-gradient(
              90deg,
              #208cc5 0%,
              #208cc5 calc(100% - 16px),
              #a3dae6 100%
            );
          }
        }
      }
    }
  }
}
</style>
