<template>
  <div id="data-view">
    <dv-full-screen-container>
      <div class="main-header">
        <div class="mh-left">
          <timerVue></timerVue>
        </div>
        <div class="mh-middle">农灵生物技术</div>
        <div class="mh-right">
          <timerVue></timerVue>
        </div>
      </div>
      <div class="scrollNum-container">
        <div class="item-scrollNum-container">
          <span>在途车辆</span>
          <FlipperVue></FlipperVue>
          <span>辆</span>
        </div>
        <div class="item-scrollNum-container">
          <span>出车趟数</span>
          <FlipperVue></FlipperVue>
          <span>次</span>
        </div>
        <div class="item-scrollNum-container">
          <span>当前计划总量</span>
          <FlipperVue></FlipperVue>
          <span>T</span>
        </div>
        <div class="item-scrollNum-container">
          <span>当前日运抵量</span>
          <FlipperVue></FlipperVue>
          <span>T</span>
        </div>
      </div>
      <dv-border-box-1 class="main-container">
        <dv-border-box-3 class="left-chart-container">

          <Left-Chart-1 />
          <Left-Chart-2 />
          <Left-Chart-3 />

        </dv-border-box-3>

        <div class="right-main-container">
          <div class="rmc-top-container">
            <dv-border-box-7 class="rmctc-left-container">

              <Center-Cmp />

            </dv-border-box-7>

            <div class="rmctc-right-container">
              <dv-border-box-3 class="rmctc-chart-1">

                <Right-Chart-1 />

              </dv-border-box-3>

              
            </div>
          </div>

          <dv-border-box-8 class="rmc-bottom-container">

            <Bottom-Charts />

          </dv-border-box-8>
        </div>
      </dv-border-box-1>

    </dv-full-screen-container>
  </div>
</template>

<script>
import LeftChart1 from './LeftChart1'
import LeftChart2 from './LeftChart2'
import LeftChart3 from './LeftChart3'

import CenterCmp from './CenterCmp'

import RightChart1 from './RightChart1'
import RightChart2 from './RightChart2'

import BottomCharts from './BottomCharts'

import timerVue from '../timer.vue'

import FlipperVue from '../Flipper.vue'
export default {
  name: 'DataView',
  components: {
    LeftChart1,
    LeftChart2,
    LeftChart3,
    CenterCmp,
    RightChart1,
    RightChart2,
    BottomCharts,
    timerVue,
    FlipperVue
  },
  data() {
    return {}
  }
}
</script>

<style lang="less">
#data-view {
  width: 100%;
  height: 100%;
  background-color: #030409;
  color: #fff;

  #dv-full-screen-container {
    background-image: url('./img/bg.png');
    background-size: 100% 100%;
    box-shadow: 0 0 3px blue;
    display: flex;
    flex-direction: column;
  }

  .main-header {
    height: 80px;
    display: flex;
    justify-content: space-between;
    align-items: flex-end;
    padding: 0 25%; //两边的间距

    .mh-left {}

    .mh-middle {
      font-size: 30px;
    }

    .mh-left,
    .mh-right {
      height: 100%;
      width: auto;
    }
  }

  .scrollNum-container {
    height: 40px;
    display: flex;
    justify-content: space-between;
    padding: 0 30px;
    margin: 20px 0;

    .item-scrollNum-container {
      display: flex;
      justify-content: center;
      align-items: center;
       color: #08e5ff;
       font-size: 20px;
       font-weight: bold;
    }
  }

  .main-container {
    height: calc(~"100% - 80px - 40px");

    .border-box-content {
      padding: 20px;
      box-sizing: border-box;
      display: flex;
    }
  }

  .left-chart-container {
    width: 26%;
    padding: 10px;
    box-sizing: border-box;

    .border-box-content {
      flex-direction: column;
    }
  }

  .right-main-container {
    width: 78%;
    padding-left: 5px;
    box-sizing: border-box;
  }

  .rmc-top-container {
    height: calc(~"65% - 10px");
    display: flex;
    margin-bottom: 10px;
  }

  .rmctc-left-container {
    width: 65%;
    margin-right: 5px;
  }

  .rmctc-right-container {
    width: 35%;
  }

  .rmc-bottom-container {
    height: calc(~"35% - 1px");
  }

  .rmctc-chart-1,
  .rmctc-chart-2 {
    height: 100%;
  }
}
</style>
