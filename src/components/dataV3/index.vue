<template>
  <div id="data-view">
    <dv-full-screen-container>
      <div class="main-header">
        <div class="mh-left">
        </div>
        <div class="mh-middle">大网运数据界面展示</div>
        <div class="mh-right">
        </div>
      </div>
      <div class="scrollNum-container">
        <div class="scrollNum-container-top">
            <LeftCenterVue></LeftCenterVue>
            <CenterCmpVue></CenterCmpVue>
            <RightCenter></RightCenter>
        </div>
        <div class="scrollNum-container-bottom">
            <RightBottomBox1Vue></RightBottomBox1Vue>
            <RightBottomBox2Vue></RightBottomBox2Vue>
            <RightBottomBox3Vue></RightBottomBox3Vue>
            <RightBottomBox4Vue></RightBottomBox4Vue>
        </div>
      </div>
    </dv-full-screen-container>
  </div>
</template>

<script>
import LeftCenterVue from './LeftCenter.vue'
import CenterCmpVue from './CenterCmp.vue'
import RightCenter from './RightCenter.vue'
import RightBottomBox1Vue from './RightBottom-box1.vue'
import RightBottomBox2Vue from './RightBottom-box2.vue'
import RightBottomBox3Vue from './RightBottom-box3.vue'
import RightBottomBox4Vue from './RightBottom-box4.vue'

export default {
  name: 'DataView',
  components: {
    LeftCenterVue,
    CenterCmpVue,
    RightCenter,
    RightBottomBox1Vue,
    RightBottomBox2Vue,
    RightBottomBox3Vue,
    RightBottomBox4Vue
  },
  data() {
    return {}
  }
}
</script>

<style lang="less" scoped>
#data-view {
  width: 100%;
  height: 100%;
  background-color: #030409;
  color: #fff;

  #dv-full-screen-container {
    background-image: url('./img/bg-3.jpg');
    background-size: 100% 100%;
    box-shadow: 0 0 3px blue;
    display: flex;
    flex-direction: column;
  }

  .main-header {
    height: 100px;
    display: flex;
    justify-content: space-between;



    .mh-left {
      background-image: url('./img/header-left.png');
      background-size: 100% 100%;
      background-repeat: no-repeat;
    }

    .mh-right {
      background-image: url('./img/header-right.png');
      background-size: 100% 100%;
      background-repeat: no-repeat;
    }

    .mh-middle {
      font-size: 30px;
      background-image: url('./img/header-center.png');
      background-size: 100% 100%;
      background-repeat: no-repeat;
      background-clip: border-box;
      height: 100%;
      width: 20%;
      display: flex;
      justify-content: center;
      align-items: center;
    }

    .mh-left,
    .mh-right {
      height: 80%;
      width: 30%;
    }
  }

  .scrollNum-container {
    height: calc(~"100% - 100px");
    padding: 10px;

    .scrollNum-container-top {
      height: 45%;
      display: flex;
      flex-direction: row;
    }

    .scrollNum-container-bottom {
      height: 55%;
      width: 100%;
      display: flex;
      align-items: flex-end;
      justify-content: space-between;
    }
  }


}
</style>
