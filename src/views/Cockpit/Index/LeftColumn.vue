<script setup lang="ts">
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
const tableData: any = [
  {
    date: '09.23 16:32:56',
    name: '隰县北',
    passageway: '隰县-吉县出入口',
    event: '车辆逆行'
  },
  {
    date: '09.23 16:32:56',
    name: '隰县北',
    passageway: '隰县-吉县出入口',
    event: '行人闯入'
  },
  {
    date: '09.23 16:32:56',
    name: '隰县北',
    passageway: '隰县-吉县出入口',
    event: '占用应急车道'
  },
  {
    date: '09.23 16:32:56',
    name: '隰县北',
    passageway: '隰县-吉县出入口',
    event: '道路拥挤'
  },
  {
    date: '09.23 16:32:56',
    name: '隰县北',
    passageway: '隰县-吉县出入口',
    event: '非法停车'
  }
]
</script>

<template>
  <div class="left-column">
    <div class="item-title">
      <span>数据统计</span>
    </div>
    <div class="data-statistics">
      <div class="column">
        <img src="@/assets/imgs/accident_icon.png" alt="" />
        <div class="column-info">
          <div class="title">
            <span>累计拥堵时长</span>
          </div>
          <div class="text">
            <span class="num linear-text">46分钟</span>
            <span class="ratio"><i class="triangle top"></i><span>3.9%</span></span>
          </div>
        </div>
      </div>
      <div class="column">
        <img src="@/assets/imgs/accident_icon.png" alt="" />
        <div class="column-info">
          <div class="title">
            <span>今日事故报警</span>
          </div>
          <div class="text">
            <span class="num linear-text">46起</span>
            <span class="ratio"><i class="triangle bottom"></i><span>3.9%</span></span>
          </div>
        </div>
      </div>
    </div>
    <div class="item-title">
      <span>拥堵排行</span>
    </div>
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
    <div class="item-title">
      <span>实时事件报警</span>
    </div>
    <div class="real-time-alarm">
      <table>
        <thead>
          <tr>
            <th>发生时间</th>
            <th>枢纽名称</th>
            <th>出入口</th>
            <th>事件类型</th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="(item, i) in tableData" :key="i">
            <td>{{ item.date }}</td>
            <td>{{ item.name }}</td>
            <td>{{ item.passageway }}</td>
            <td>{{ item.event }}</td>
          </tr>
        </tbody>
      </table>
    </div>
  </div>
</template>

<style lang="less" scoped>
.left-column {
  width: 532px;
  padding: 20px 34px;
  background-image: url('/src/assets/imgs/L.png');
  background-size: 100% 100%;

  .data-statistics {
    display: flex;
    padding: 30px 0;
    justify-content: space-between;

    .column {
      display: flex;
      width: 45%;

      > img {
        width: 100px;
        height: auto;
      }

      .column-info {
        padding-top: 15px;
      }

      .title {
        width: 120px;
        height: 22px;
        background: linear-gradient(90deg, #008efb 0%, rgba(0, 59, 104, 0) 100%);
        border-radius: 2px 0px 0px 2px;
        padding-left: 8px;
        line-height: 21px;
        color: #ffffff;
        span {
          font-size: 14px;
          letter-spacing: 1px;
          padding-right: 3px;
          font-weight: bold;
          background: linear-gradient(180deg, #ffffff 0%, #56d8ff 100%);
          -webkit-background-clip: text;
          -webkit-text-fill-color: transparent;
        }
      }
      .text {
        white-space: nowrap;
        line-height: 1;
        padding-top: 9px;
        .num {
          font-size: 18px;
          line-height: 27px;
          letter-spacing: 1px;
          background: linear-gradient(180deg, #ffffff 0%, #56d8ff 100%);
          -webkit-background-clip: text;
          -webkit-text-fill-color: transparent;
        }
      }

      .ratio {
        padding-left: 5px;
        color: #ffffff;
        white-space: nowrap;
        i.triangle {
          display: inline-block;
          border-bottom: 4px solid #7cff92;
          border-left: 4px solid transparent;
          border-right: 4px solid transparent;
          margin-right: 2px;
          &.bottom {
            border-bottom-color: #da2007;
            transform: rotate(180deg);
          }
        }
        span {
          display: inline-block;
          transform: scale(0.8);
        }
      }
    }
  }

  .jam-top {
    padding: 15px 0 30px;
    font-size: 12px;

    li {
      padding: 11px 0;

      .info-row {
        display: flex;
        justify-content: space-between;

        .label {
          font-size: 14px;
          padding-left: 10px;
          color: #eff8ff;
        }
        .linear-text {
          font-size: 18px;
          padding-right: 2px;
          letter-spacing: 1px;

          background: linear-gradient(180deg, #ffffff 0%, #56d8ff 100%);
          -webkit-background-clip: text;
          -webkit-text-fill-color: transparent;
        }
      }

      .bar-row {
        height: 8px;
        margin-top: 2px;
        background-color: rgba(113, 166, 204, 0.3);
        box-shadow: 0 0 2px rgba(0, 0, 0, 0.2);

        .bar {
          height: 100%;
          background-color: rgba(255, 255, 255, 0.8);
          background-image: linear-gradient(
            90deg,
            rgba(28, 181, 255, 0.8) 0%,
            rgba(28, 181, 255, 0.8) calc(100% - 21px),
            rgba(29, 193, 224, 0) 100%
          );
        }
      }
    }
  }

  .real-time-alarm {
    color: #ffffff;
    font-size: 16px;
    background-image: url('/src/assets/imgs/table_bg.png');
    background-size: 100% auto;
    margin-top: 25px;
    table {
      width: 100%;
      text-align: center;
    }
    tr {
      td:first-of-type {
        font-family: D-DIN;
      }
    }
    th {
      font-weight: bold;
      letter-spacing: 1px;
      height: 43px;
    }
    td {
      height: 45px;
    }
  }
}
</style>
