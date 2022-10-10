<script setup lang="ts">
import { ref } from 'vue'
import Hub from './Hub.vue'
import { ElDialog } from 'element-plus'
// console.log(ClickOutside)

defineProps({
  left: {
    type: [String, Number],
    default: 0
  },
  top: {
    type: [String, Number],
    default: 0
  },
  number: {
    type: Number,
    default: 1
  },
  name: {
    type: String,
    default: ''
  }
})

const dialogVisible = ref<boolean>(false)

// 立即处理弹窗
const immediateHandle = () => {
  dialogVisible.value = true
}
const handleClose = () => {
  dialogVisible.value = false
}
</script>

<template>
  <div class="point-hub" :style="`left: ${left}; top: ${top}`">
    <div class="hub-name">
      <span class="index">{{ number }}</span>
      <span class="name">{{ name }}</span>
    </div>
    <ul class="ramp-group">
      <Hub left="-10px" top="-10px" @immediate="immediateHandle" />
      <Hub right="-10px" top="-10px" @immediate="immediateHandle" />
      <Hub right="-20px" bottom="-20px" @immediate="immediateHandle" type="alarm" />
      <Hub left="-10px" bottom="-10px" @immediate="immediateHandle" />
    </ul>
  </div>
  <el-dialog
    v-model="dialogVisible"
    title="事件处置"
    class="cockpit-dialog"
    width="854px"
    :before-close="handleClose"
  >
    <template #header>
      <div class="header-content">
        <span class="title">事件处置</span>
        <span class="text-shadow">事件处置</span>
      </div>
    </template>
    <div class="dialog-content">
      <div class="info-column">
        <ul>
          <li class="row">
            <span class="label">事件类型：</span>
            <span class="value"> <input type="text" value="交通拥堵" /> </span>
          </li>
          <li class="row">
            <span class="label">事件位置：</span>
            <span class="value"> <input type="text" value="大宁互通K57+110" /> </span>
          </li>
          <li class="row">
            <span class="label">方向：</span>
            <span class="value"> <input type="text" value="上行" /> </span>
          </li>
          <li class="row">
            <span class="label">报警设备：</span>
            <span class="value"> <input type="text" value="摄像头（K1196+693)" /> </span>
          </li>
          <li class="row">
            <span class="label">报警时间：</span>
            <span class="value"> <input type="text" value="2022/10/04 12:13:14" /> </span>
          </li>
          <li class="row">
            <span class="label">修改事件类型：</span>
            <span class="value"> <input type="text" value="道路拥堵" /> </span>
          </li>
        </ul>
      </div>
      <div class="tab-column"></div>
    </div>
    <template #footer>
      <span class="dialog-footer">
        <button @click="dialogVisible = false">
          <span>误报</span>
        </button>
        <button @click="dialogVisible = false">
          <span>忽略</span>
        </button>
        <button @click="dialogVisible = false">
          <span>确认事件</span>
        </button>
      </span>
    </template>
  </el-dialog>
</template>

<style lang="less" scoped>
.point-hub {
  height: 75px;
  width: 67px;
  position: absolute;
  background-image: url('/src/assets/imgs/point_hub.png');
  background-size: 100% auto;
  background-repeat: no-repeat;
  .hub-name {
    width: 195px;
    height: 35px;
    background-image: url('/src/assets/imgs/hub_name.png');
    background-size: 100% 100%;
    background-repeat: no-repeat;
    position: absolute;
    right: 70px;
    display: flex;
    text-align: center;
    .index {
      width: 35px;
      line-height: 35px;
      color: #07213d;
      font-size: 17px;
    }
    .name {
      width: 160px;
      line-height: 35px;
      font-size: 20px;
      color: #ffffff;
    }
  }
  .ramp-group {
    position: relative;
    margin-top: 50%;
    width: 100%;
    height: 60%;
  }
}
.cockpit-dialog {
  .header-content {
    font-family: pangmen;
    font-size: 28px;
    letter-spacing: 2px;
    padding-left: 20px;
    .title {
      background: linear-gradient(180deg, #ffffff 0%, #4eb3ff 100%);
      -webkit-background-clip: text;
      -webkit-text-fill-color: transparent;
      position: absolute;
    }
    .text-shadow {
      color: transparent;
      text-shadow: 0px 2px 0px #233444;
    }
  }
  .dialog-content {
    height: 100%;
    display: flex;
    .info-column {
      li {
        height: 79px;
        display: flex;
        align-items: center;
        & + li {
          margin-top: -15px;
        }
        .label {
          width: 120px;
          text-align: right;
          font-size: 14px;
          color: #9ebdde;
        }
        .value {
          height: 79px;
          width: 248px;

          background-image: url('/src/assets/imgs/value_bg.png');
          background-size: 100% auto;
          background-repeat: no-repeat;
          input {
            width: 190px;
            margin-left: 26px;
            margin-top: 29px;
            padding-left: 14px;
            font-size: 14px;
            background: linear-gradient(180deg, #ffffff 0%, #56d8ff 100%);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            &:focus {
              outline: none;
            }
          }
        }
      }
    }
    .tab-column {
      width: calc(100% - 300px);
    }
  }
  .dialog-footer {
    button {
      width: 122px;
      height: 42px;

      background-image: url('/src/assets/imgs/button_bg.png');
      background-size: 100% auto;
      background-repeat: no-repeat;
      & + button {
        margin-left: 14px;
      }
      span {
        font-family: pangmen;
        font-size: 18px;
        letter-spacing: 1px;
        background: linear-gradient(180deg, #ffffff 0%, #56d8ff 100%);
        -webkit-background-clip: text;
        -webkit-text-fill-color: transparent;
      }
    }
  }
}
</style>

<style lang="less">
.el-dialog.cockpit-dialog {
  --el-dialog-margin-top: 250px;
  --el-dialog-bg-color: transparent;
  background-image: url('/src/assets/imgs/dialog_bg.png');
  background-size: 100% auto;
  box-shadow: 0 0 50px rgba(19, 213, 255, 0.3);
  height: 588px;
  .el-dialog__header {
    padding-top: 15px;
    padding-bottom: 5px;
    .el-dialog__close,
    .el-dialog__close svg {
      width: 2em;
      height: 2em;
      color: #34c7f8;
    }
    .el-dialog__headerbtn {
      top: 9px;
      right: 7px;
    }
  }
  .el-dialog__body {
    height: 450px;
  }
  .el-dialog__footer {
    text-align: center;
    height: 75px;
    padding: 0;
  }
}
</style>
