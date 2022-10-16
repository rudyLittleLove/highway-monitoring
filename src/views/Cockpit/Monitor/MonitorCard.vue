<script setup lang="ts">
// import { ref } from 'vue'
// import Hub from './Hub.vue'
// import { ElDialog } from 'element-plus'
// console.log(ClickOutside)

defineProps({
  placement: {
    type: String,
    default: 'left'
  }
})
</script>

<template>
  <div class="monitor-card" :class="`placement-${placement}`">
    <div class="monitor-box">
      <div class="monitor-card-header">隰县北互通上行方向 入口</div>
      <div class="monitor-card-body">
        <div class="monitor-item-title">
          <span>匝道路况</span>
        </div>
        <ul class="monitor-card-content">
          <li>分合流车辆数：15辆</li>
          <li>排队长度：60M</li>
          <li>平均速度：12km/h</li>
          <li>
            拥堵程度：
            <span class="green">基本畅通</span>
          </li>
        </ul>
      </div>
    </div>
    <div class="monitor-equipment" v-if="['left-top', 'right-bottom'].includes(placement)">
      <span class="angle"></span>
      <span class="angle"></span>
      <span class="angle"></span>
      <span class="angle"></span>

      <div class="content">
        <img src="/src/assets/imgs/monitor.png" width="66" alt="" />
        <Icon icon="ep:d-arrow-left" :size="24" class="cursor-pointer anticon" color="#40FE81" />

        <ul class="info">
          <li>1号监控设备</li>
          <li>
            设备状态：
            <span class="green">在线</span>
          </li>
        </ul>
      </div>

      <div class="connect-link"></div>
    </div>
  </div>
</template>

<style lang="less" scoped>
.monitor-card {
  position: absolute;
  .monitor-box {
    width: 330px;
    height: 228px;
    background-image: url('/src/assets/imgs/dialog_bg.png');
    background-size: 100% auto;

    box-shadow: 0 0 30px rgba(19, 213, 255, 0.3);

    .monitor-card-header {
      padding-left: 25px;
      padding-top: 2px;
      font-size: 16px;
      letter-spacing: 1px;

      background: linear-gradient(180deg, #ffffff 0%, #4eb3ff 100%);
      -webkit-background-clip: text;
      -webkit-text-fill-color: transparent;
    }
    .monitor-card-body {
      padding-left: 25px;
      padding-top: 25px;

      .monitor-item-title {
        background-image: url('/src/assets/imgs/hub_title_bg.png');
        background-size: 100% auto;
        height: 26px;
        padding-left: 30px;

        span {
          font-size: 14px;
          background: linear-gradient(180deg, #ffffff 0%, #4eb3ff 100%);
          -webkit-background-clip: text;
          -webkit-text-fill-color: transparent;
        }
      }

      .monitor-card-content {
        padding-top: 13px;
        li {
          padding: 8px 0;
          font-size: 14px;
          line-height: 1;
          color: #9ebdde;
          padding-left: 25px;
          &::before {
            content: '';
            float: left;
            width: 8px;
            height: 8px;
            margin-left: -20px;
            margin-right: 10px;
            margin-top: 2px;
            background-color: #3ef6ff;
            transform: rotate(45deg);
            box-shadow: 0px 0px 4px 0px #3ef6ff;
          }
        }
      }
    }
  }

  .green {
    color: #51ff8d;
  }
  .orange {
    color: #e96903;
  }
  .yellow {
    color: #dfff3a;
  }
  .red {
    color: #ff0101;
  }

  .monitor-equipment {
    width: 245px;
    height: 76px;
    background: rgba(1, 42, 60, 0.5);
    border: 1px solid rgba(27, 208, 254, 0.5);
    position: absolute;

    .angle {
      position: absolute;
      width: 14px;
      height: 14px;
      border: 1px solid #1bd0fe;
      &:nth-of-type(1) {
        left: -1px;
        top: -1px;
        border-right: none;
        border-bottom: none;
      }
      &:nth-of-type(2) {
        right: -1px;
        top: -1px;
        border-left: none;
        border-bottom: none;
      }
      &:nth-of-type(3) {
        right: -1px;
        bottom: -1px;
        border-left: none;
        border-top: none;
      }
      &:nth-of-type(4) {
        left: -1px;
        bottom: -1px;
        border-right: none;
        border-top: none;
      }
    }

    .connect-link {
      width: 78px;
      height: 205px;
      border-top: 1px solid #12d5ff;
      border-right: 1px solid #12d5ff;
      position: absolute;

      &::before {
        content: '';
        position: absolute;

        margin-left: -8px;
        margin-top: -8px;

        width: 16px;
        height: 16px;
        background: #defbff;
        box-sizing: border-box;
        border-radius: 50%;
        border: 3px solid #2fcad9;
        outline: 4px solid rgba(27, 208, 254, 0.16);
      }
      &::after {
        content: '';
        position: absolute;
        width: 17px;
        height: 17px;
        background: #1bd0fe;

        left: 100%;
        top: 100%;
        margin-left: -8px;
        border-radius: 50%;
      }
    }
    .content {
      width: 100%;
      height: 100%;
      display: flex;
      align-items: center;
      justify-content: space-between;
      img {
        margin-left: 16px;
        flex-shrink: 0;
      }
      .cursor-pointer {
        transform: rotate(-90deg);
      }
      .info {
        color: #defbff;
        font-size: 16px;
        margin-right: 10px;
        font-family: siyuan;
        li {
          padding: 2px 0;
        }
      }
    }
  }

  &.placement-left-top {
    left: 0;
    top: 0;
    .monitor-equipment {
      left: 350px;
      top: 17px;
      .connect-link {
        left: 100%;
        top: 50%;
      }
    }
  }
  &.placement-left-bottom {
    left: 0;
    bottom: 0;
  }
  &.placement-right-top {
    right: 0;
    top: 0;
  }
  &.placement-right-bottom {
    right: 0;
    bottom: 0;
    .monitor-equipment {
      right: 350px;
      bottom: 17px;
      .connect-link {
        transform-origin: 0 0;
        transform: rotate(180deg);
        // right: 100%;
        top: 40px;
      }
    }
  }
}
</style>
