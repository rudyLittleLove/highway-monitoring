<script setup lang="ts">
import { ref, unref, watch } from 'vue'
import { ElPopover } from 'element-plus'

// console.log(ClickOutside)

const props = defineProps({
  left: {
    type: [String, Number],
    default: ''
  },
  top: {
    type: [String, Number],
    default: ''
  },
  right: {
    type: [String, Number],
    default: ''
  },
  bottom: {
    type: [String, Number],
    default: ''
  },
  type: {
    type: String,
    default: ''
  }
})

const buttonRef = ref()

const popoverRef = ref()
const dialogClassName = ref<string>('hub-popper')

watch(
  () => props.type,
  (val: string) => {
    if (dialogClassName.value) {
      dialogClassName.value = val === 'alarm' ? 'hub-alarm-popper' : 'hub-popper'
    }
  },
  {
    immediate: true
  }
)

const closeDialog = () => {
  unref(popoverRef)?.hide()
}

const emit = defineEmits(['immediate'])

const immediateHandle = () => {
  closeDialog()
  emit('immediate')
}
</script>

<template>
  <li
    ref="buttonRef"
    class="hub-item"
    :class="type"
    :style="`left: ${left}; top: ${top}; right: ${right}; bottom: ${bottom};`"
  ></li>
  <el-popover
    ref="popoverRef"
    :popper-class="dialogClassName"
    :virtual-ref="buttonRef"
    :show-arrow="false"
    :teleported="false"
    :offset="50"
    placement="right-start"
    trigger="click"
    virtual-triggering
  >
    <div class="normal" v-if="dialogClassName === 'hub-popper'">
      <div class="header">
        <span class="title">上行方向出口实时视频</span>
        <span class="close" @click="closeDialog"></span>
      </div>
      <div class="body"></div>
    </div>

    <div class="alarm" v-else>
      <div class="header">
        <span class="title">交通事故报警</span>
        <span class="close" @click="closeDialog"></span>
      </div>
      <div class="body"></div>
      <div class="footer" @click="immediateHandle">立即处理</div>
    </div>
  </el-popover>
</template>

<style lang="less" scoped>
.hub-item {
  position: absolute;
  width: 25px;
  height: 27px;
  background-image: url('/src/assets/imgs/ramp.png');
  background-size: 100% auto;
  background-repeat: no-repeat;
  cursor: pointer;
  &.alarm {
    width: 42px;
    height: 46px;
    background-image: url('/src/assets/imgs/ramp_alarm.png');
  }
}
// 实时监控弹窗样式
.hub-popper {
  .normal {
    height: 100%;
    .header {
      height: 31px;
      padding-left: 12px;
      .title {
        font-family: pangmen;
        line-height: 32px;
        font-size: 20px;
        letter-spacing: 1px;
        background: linear-gradient(360deg, #21b6db 0%, #ffffff 100%);
        -webkit-background-clip: text;
        -webkit-text-fill-color: transparent;
      }
      .close {
        float: right;
        width: 15px;
        height: 15px;
        margin-right: 23px;
        margin-top: 10px;
        cursor: pointer;
      }
    }
    .body {
      margin-left: 2px;
      width: 352px;
      height: 176px;
      background-color: #ffffff;
    }
  }
}

// 告警弹窗样式
.hub-alarm-popper {
  .alarm {
    .header {
      height: 44px;
      .title {
        float: left;
        margin-top: 14px;
        margin-left: 22px;
        font-family: pangmen;
        line-height: 32px;
        font-size: 20px;
        letter-spacing: 1px;
        background: linear-gradient(360deg, #de8387 0%, #ffffff 100%);
        -webkit-background-clip: text;
        -webkit-text-fill-color: transparent;
      }
      .close {
        float: right;
        width: 25px;
        height: 25px;
        border-radius: 50%;
        cursor: pointer;
      }
    }
    .body {
      width: 175px;
      height: 145px;
      margin-top: 6px;
      margin-left: 27px;
      background-color: #ffffff;
    }
    .footer {
      font-family: 微软雅黑;
      font-weight: bold;
      font-size: 20px;
      text-align: center;
      margin-top: 8px;
      margin-right: 7px;
      cursor: pointer;

      background: linear-gradient(360deg, #f08919 0%, #ffe15e 100%);
      -webkit-background-clip: text;
      -webkit-text-fill-color: transparent;
    }
  }
}
</style>

<style lang="less">
// 实时监控弹窗样式
.el-popper.el-popover.hub-popper {
  padding: 0;
  width: 367px !important;
  height: 224px;
  border-radius: 0;
  border: none;
  background-color: transparent;
  background-image: url('/src/assets/imgs/hub_dialog_bg.png');
  background-size: 100% 100%;
}
// 告警弹窗样式
.el-popper.el-popover.hub-alarm-popper {
  padding: 0;
  width: 237px !important;
  height: 260px;
  border-radius: 0;
  border: none;
  background-color: transparent;
  background-image: url('/src/assets/imgs/hub_alarm_dialog_bg.png');
  background-size: 100% 100%;
}
</style>
