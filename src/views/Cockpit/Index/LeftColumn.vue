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
    <div class="item-title">数据统计</div>
    <div class="data-statistics">
      <div class="column">
        <img src="@/assets/imgs/accident_icon.png" alt="" />
        <div class="column-info">
          <div class="title">累计拥堵时长</div>
          <div class="text">
            <span class="num linear-text">46分钟</span>
            <span class="ratio"><i class="triangle top"></i>3.9%</span>
          </div>
        </div>
      </div>
      <div class="column">
        <img src="@/assets/imgs/accident_icon.png" alt="" />
        <div class="column-info">
          <div class="title">今日事故报警</div>
          <div class="text">
            <span class="num linear-text">46起</span>
            <span class="ratio"><i class="triangle bottom"></i>3.9%</span>
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
      .text {
        white-space: nowrap;
      }

      .ratio {
        padding-left: 5px;
        font-size: 12px;
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

        .label {
          padding-left: 10px;
          color: #ffffff;
        }
        .linear-text {
          padding-right: 2px;
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

  .real-time-alarm {
    color: #ffffff;
    font-style: italic;
    font-size: 12px;
    background-image: url('/src/assets/imgs/table_bg.png');
    background-size: 100% auto;
    height: 205px;
    margin-top: 15px;
    table {
      width: 100%;
      text-align: center;
    }
    th {
      font-weight: bold;
      height: 32px;
    }
    td {
      height: 34px;
    }
  }
}
</style>
