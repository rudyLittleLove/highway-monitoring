<script setup lang="ts">
import { ref } from 'vue'
import { ElRow, ElCol, ElCard, ElTabs, ElTabPane, ElInput, ElButton } from 'element-plus'

const activeName = ref<string>('realtime')
const iconColor = '#1890FF'
const order = ref<boolean>(true)
const handleClick = () => {
  console.log(11)
}
</script>

<template>
  <el-row :gutter="12" class="road-to-wrap">
    <el-col :span="7">
      <el-card class="box-card">
        <template #header>
          <div class="card-header">
            <span>实时拥堵路况</span>
            <Icon
              icon="ant-design:caret-up-outlined"
              :size="14"
              class="cursor-pointer"
              :color="order ? iconColor : ''"
              @click="order = true"
            />
            <Icon
              icon="ant-design:caret-down-outlined"
              :size="14"
              class="cursor-pointer"
              :color="!order ? iconColor : ''"
              @click="order = false"
            />
            <!-- <el-button class="button" text>Operation button</el-button> -->
          </div>
        </template>
        <el-tabs v-model="activeName" type="card" stretch @tab-click="handleClick">
          <el-tab-pane label="实时拥堵" name="realtime" />
          <el-tab-pane label="昨日" name="yesterday" />
          <el-tab-pane label="上月" name="ultimo" />
        </el-tabs>
        <el-input class="search-input" placeholder="请输入要查询的枢纽">
          <template #append>
            <el-button>
              <Icon icon="ep:search" color="#ffffff" />
            </el-button>
          </template>
        </el-input>
      </el-card>
    </el-col>
    <el-col :span="17">
      <el-card class="" />
    </el-col>
  </el-row>
</template>

<style lang="less" scoped>
.road-to-wrap {
  height: 100%;
  .el-card {
    height: 100%;
  }
  .card-header {
    display: flex;
    align-items: center;
    height: 33px;
    color: rgba(0, 0, 0, 0.65);

    > .el-icon {
      &:nth-of-type(1) {
        margin-left: 5px;
        margin-top: -8px;
      }
      &:nth-of-type(2) {
        margin-bottom: -8px;
        margin-left: -14px;
      }
    }
  }
  :deep(.el-tabs--card) {
    .el-card__body {
      padding: 14px;
    }
    > .el-tabs__header {
      margin-bottom: 0;
    }
    .el-tabs__item.is-active {
      background-color: #ffffff;
      // border-top-left-radius: 4px;
      // border-top-right-radius: 4px;
      line-height: 36px;
      border-top: 2px solid #1890ff;
    }
  }

  .search-input {
    margin-top: 16px;
    :deep(.el-input__wrapper) {
      box-shadow: 0 0 0 1px #eff2f5;
    }
    :deep(.el-input-group__append) {
      background-color: #1890ff;
      border-radius: 0;
      .el-button {
        border-radius: 0;
        border-color: #1890ff;
      }
    }
  }
}
</style>
