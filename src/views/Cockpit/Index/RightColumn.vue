<script setup lang="ts">
import { Echart } from '@/components/Echart'
import { EChartsOption } from 'echarts'
import * as echarts from 'echarts'

const chartOriginData: any = [
  {
    label: '隰县北互通',
    data: [100, 150, 130, 180, 150, 170, 90]
  },
  {
    label: '寨子互通',
    data: [110, 180, 200, 210, 160, 180, 100]
  },
  {
    label: '午城互通',
    data: [120, 190, 210, 240, 190, 190, 110]
  },
  {
    label: '大宁互通',
    data: [121, 192, 220, 250, 200, 210, 120]
  },
  {
    label: '窑头互通',
    data: [130, 230, 350, 390, 240, 260, 150]
  }
]

const chartData1: EChartsOption = {
  color: ['#8de7f6', '#86ffbe', '#657fff', '#e3ff97', '#ff8944'],
  // tooltip: {
  //   trigger: 'axis'
  // },
  legend: {
    data: chartOriginData.map((v: any) => v.label),
    icon: 'path://M512 1024C229.230208 1024 0 794.769792 0 512 0 229.230208 229.230208 0 512 0 794.769792 0 1024 229.230208 1024 512 1024 794.769792 794.769792 1024 512 1024ZM512 960C759.423565 960 960 759.423565 960 512 960 264.576432 759.423565 64 512 64 264.576432 64 64 264.576432 64 512 64 759.423565 264.576432 960 512 960ZM512 832C688.731117 832 832 688.731117 832 512 832 335.26888 688.731117 192 512 192 335.26888 192 192 335.26888 192 512 192 688.731117 335.26888 832 512 832Z',
    bottom: 0,
    itemWidth: 14,
    itemGap: 20,
    padding: 0,
    textStyle: {
      color: '#ffffff',
      fontSize: 12,
      padding: [0, 0, -2, 0],
      rich: {
        a: {
          verticalAlign: 'bottom'
        }
      }
    }
  },
  grid: {
    top: '10px',
    left: 0,
    right: '20px',
    bottom: '35px',
    containLabel: true
  },
  xAxis: {
    type: 'category',
    boundaryGap: false,
    data: ['0:00', '4:00', '8:00', '12:00', '16:00', '20:00', '24:00'],
    axisLine: {
      lineStyle: {
        color: '#1e3851'
      }
    },
    axisLabel: {
      color: '#E2EAFF',
      fontSize: 14
    },
    axisTick: {
      show: false
    }
  },
  yAxis: {
    type: 'value',
    axisLabel: {
      color: '#E2EAFF',
      fontSize: 14
    },
    splitLine: {
      lineStyle: {
        type: 'dashed',
        color: '#213c54'
      }
    }
  },
  series: chartOriginData.map((v: any) => ({
    name: v.label,
    type: 'line',
    smooth: true,
    symbolSize: 0,
    lineStyle: {
      width: 1.5,
      shadowColor: 'rgba(0,0,0,0.3)',
      shadowBlur: 1,
      shadowOffsetY: 2,
      shadowOffsetX: 1
    },
    data: v.data
  }))
}

const percent: any = [
  {
    label: '车辆逆行',
    value: '28',
    ratio: '28%',
    linear: 'linear-gradient(180deg, #20A6FA 0%, rgba(0, 132, 231, 0.3) 100%);',
    color: 'rgba(25, 151, 230, 0.2)'
  },
  {
    label: '行人闯入',
    value: '12',
    ratio: '12%',
    linear: 'linear-gradient(180deg, #9AC3FF  0%, rgba(62, 78, 134, 0.6) 100%);',
    color: 'rgba(154, 195, 255, 0.2)'
  },
  {
    label: '占用应急车道',
    value: '5',
    ratio: '5%',
    linear: 'linear-gradient(180deg, #00F1FF 0%, rgba(0, 222, 255, 0.3) 100%);',
    color: 'rgba(0, 222, 255, 0.2)'
  },
  {
    label: '道路堵塞',
    value: '9',
    ratio: '9%',
    linear: 'linear-gradient(180deg, #FF7F50 0%, rgba(255, 127, 80, 0.3) 100%);',
    color: 'rgba(255, 127, 80, 0.2)'
  },
  {
    label: '非法停车',
    value: '2',
    ratio: '2%',
    linear: 'linear-gradient(180deg, #DDDB00 0%, rgba(166, 157, 0, 0.3) 100%);',
    color: 'rgba(255, 253, 0, 0.2)'
  },
  {
    label: '交通事故',
    value: '18',
    ratio: '18%',
    linear: 'linear-gradient(180deg, #9AC3FF  0%, rgba(62, 78, 134, 0.6) 100%);',
    color: 'rgba(154, 195, 255, 0.2)'
  },
  {
    label: '交通事件总数',
    value: '50',
    ratio: '72',
    linear: 'linear-gradient(180deg, #20A6FA 0%, rgba(0, 132, 231, 0.3) 100%);',
    color: 'rgba(25, 151, 230, 0.2)'
  }
]

const color: string[] = ['#8de7f6', '#86ffbe', '#657fff', '#e3ff97', '#ff8944']
const chartData2: EChartsOption = {
  color: color,
  // tooltip: {
  //   trigger: 'axis'
  // },
  legend: {
    data: chartOriginData.map((v: any) => v.label),
    icon: 'path://M512 1024C229.230208 1024 0 794.769792 0 512 0 229.230208 229.230208 0 512 0 794.769792 0 1024 229.230208 1024 512 1024 794.769792 794.769792 1024 512 1024ZM512 960C759.423565 960 960 759.423565 960 512 960 264.576432 759.423565 64 512 64 264.576432 64 64 264.576432 64 512 64 759.423565 264.576432 960 512 960ZM512 832C688.731117 832 832 688.731117 832 512 832 335.26888 688.731117 192 512 192 335.26888 192 192 335.26888 192 512 192 688.731117 335.26888 832 512 832Z',
    bottom: 0,
    itemGap: 20,
    itemWidth: 14,
    padding: 0,
    textStyle: {
      color: '#ffffff',
      fontSize: 12,
      padding: [0, 0, -2, 0],
      rich: {
        a: {
          verticalAlign: 'bottom'
        }
      }
    }
  },
  grid: {
    top: '10px',
    left: 0,
    right: '20px',
    bottom: '35px',
    containLabel: true
  },
  xAxis: {
    type: 'category',
    boundaryGap: false,
    data: ['0:00', '4:00', '8:00', '12:00', '16:00', '20:00', '24:00'],
    axisLine: {
      lineStyle: {
        color: '#1e3851'
      }
    },
    axisLabel: {
      color: '#d4dcea',
      fontSize: 14
    },
    axisTick: {
      show: false
    },
    splitLine: {
      show: true,
      lineStyle: {
        color: '#213c54'
      }
    }
  },
  yAxis: {
    type: 'value',
    axisLabel: {
      color: '#e4ebfb',
      fontSize: 14
    },
    splitLine: {
      lineStyle: {
        color: '#213c54'
      }
    }
  },
  series: chartOriginData.map((v: any, i: number) => ({
    name: v.label,
    type: 'line',
    smooth: true,
    showSymbol: false,
    lineStyle: {
      width: 1.5,
      shadowColor: 'rgba(0,0,0,0.3)',
      shadowBlur: 1,
      shadowOffsetY: 2,
      shadowOffsetX: 1
    },
    areaStyle: {
      opacity: 0.2,
      color: new echarts.graphic.LinearGradient(0, 0, 0, 1, [
        {
          offset: 0,
          color: color[i]
        },
        {
          offset: 1,
          color: color[i] + '11'
        }
      ])
    },
    data: v.data
  }))
}
</script>

<template>
  <div class="right-column">
    <div class="item-title">
      <span>断面通行车辆数</span>
    </div>
    <div class="passing-cars">
      <div class="chart-header">
        <div class="chart-title">断面车流量（辆）</div>
        <div class="tab-switch">
          <div class="active">上行方向</div>
          <div>下行方向</div>
        </div>
      </div>
      <Echart :options="chartData1" :height="200" />
    </div>
    <div class="item-title">
      <span>交通事件占比</span>
    </div>
    <div class="traffic-incidents-percent">
      <ul>
        <li
          v-for="(item, i) in percent"
          :key="i"
          :style="`width: ${item.value * 2}px;height: ${item.value * 2}px; background-image: ${
            item.linear
          }; outline: ${5 * (item.value / 80 + 1)}px solid ${item.color}`"
        >
          <span class="value" :style="`font-size: ${item.value / 2}px`">{{ item.ratio }}</span>
          <span class="label">{{ item.label }}</span>
        </li>
      </ul>
    </div>
    <div class="item-title">
      <span>车型分布</span>
    </div>
    <div class="car-type-distribute">
      <div class="chart-header">
        <div class="chart-title linear-text">车辆数（辆）</div>
        <div class="tab-switch">
          <div class="active">大客车</div>
          <div>小客车</div>
          <div>货车</div>
        </div>
      </div>
      <Echart :options="chartData2" :height="200" />
    </div>
  </div>
</template>

<style lang="less" scoped>
.right-column {
  width: 532px;
  padding: 20px 34px;
  background-image: url('/src/assets/imgs/L.png');
  background-size: 100% 100%;

  .chart-header {
    display: flex;
    justify-content: space-between;
    padding-top: 20px;
    padding-bottom: 20px;
    .chart-title {
      font-size: 14px;
      font-weight: bold;

      letter-spacing: 1px;
      background: linear-gradient(180deg, #f8f9fa 0%, #8ae4ff 100%);
      -webkit-background-clip: text;
      -webkit-text-fill-color: transparent;
    }
    .tab-switch {
      display: flex;
      font-size: 14px;
      color: #ffffff;
      > div {
        padding-right: 3px;
        height: 20px;
        width: 90px;
        margin-right: -10px;
        text-align: center;
        cursor: pointer;
        &:not(.active) {
          background-image: -webkit-linear-gradient(top, #ffffff, #7df6ff);
          -webkit-background-clip: text;
          -webkit-text-fill-color: transparent;
        }
        &.active {
          background-image: url('/src/assets/imgs/tab_active.png');
          background-size: 100% 100%;
        }
      }
    }
  }
  .passing-cars {
    margin-bottom: 40px;
  }

  .traffic-incidents-percent {
    height: 182px;
    background-image: url('/src/assets/imgs/bubble_bg.png');
    background-size: 100% 100%;
    margin-bottom: 20px;
    margin-top: 20px;
    > ul {
      width: 100%;
      height: 100%;
      position: relative;
      > li {
        border-radius: 50%;
        position: absolute;
        min-width: 20px;
        min-height: 20px;
        text-align: center;
        .value {
          color: #ffffff;
          position: absolute;
          left: 50%;
          top: 50%;
          transform: translateX(-50%) translateY(-50%);
        }
        .label {
          white-space: nowrap;
          position: absolute;
          bottom: -25px;
          color: #43c4ff;
          font-size: 12px;
          transform: translateX(-50%) scale(0.8);
        }
        &:nth-of-type(1) {
          left: 5%;
          top: 30%;
        }
        &:nth-of-type(2) {
          left: 25%;
          top: 10%;
        }
        &:nth-of-type(3) {
          left: 23%;
          top: 60%;
        }
        &:nth-of-type(4) {
          left: 75%;
          top: 10%;
        }
        &:nth-of-type(5) {
          left: 70%;
          top: 65%;
        }
        &:nth-of-type(6) {
          left: 85%;
          top: 50%;
        }
        &:nth-of-type(7) {
          left: 50%;
          top: 50%;
          transform: translateX(-50%) translateY(-50%);
        }
      }
    }
  }

  .car-type-distribute {
  }
}
</style>
