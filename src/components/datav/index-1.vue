<template>
  <div id="data-view">
    <dv-full-screen-container>
      <div class="main-header zindex">
        <div class="mh-middle">农灵生物技术数据监测分析平台</div>
        <div class="mh-right">
          <timerVue></timerVue>
        </div>
      </div>
      <div class="scrollNum-container zindex">
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
      <dv-border-box-1 class="main-container ">
        <dv-border-box-3 class="left-chart-container">

          <!-- <Left-Chart-1 />
          <Left-Chart-2 />
          <Left-Chart-3 /> -->

        </dv-border-box-3>

        <div class="right-main-container">
          <div class="rmc-top-container">
            <dv-border-box-7 class="rmctc-left-container">

              <!-- <Center-Cmp /> -->

            </dv-border-box-7>

            <div class="rmctc-right-container">
              <dv-border-box-3 class="rmctc-chart-1 zindex">

                <Right-Chart-1 />

              </dv-border-box-3>


            </div>
          </div>

          <dv-border-box-8 class="rmc-bottom-container zindex">

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

import FlopVue from '../Flop.vue'

import AMapLoader from '@amap/amap-jsapi-loader';

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
    FlipperVue,
    FlopVue
  },
  data() {
    return {
      map: null,
      aMapUI: null,
    }
  },
  async mounted() {
    await this.initMap()
    await this.initMapUi()
  },
  methods: {
    initMap() {
      AMapLoader.load({
        key: 'd43ef4aa593c951f5ae495473472e8ea', // key
        plugins: ["AMap.Geocoder", 'Map3D'], // 插件
        version: '2.0', // 版本
        Loca: { // 是否加载 Loca， 缺省不加载
          "version": '2.0.0'  // Loca 版本，缺省 1.3.2
        },
        AMapUI: {//重点就是这个，这个是加载AMapUI的
          version: '1.1',//AMapUI的版本号
          plugins: ['misc/PathSimplifier', 'overlay/SimpleMarker']//SimpleMarker设置自定义图标，PathSimplifier轨迹展示组件
        }
      }).then((amap, b) => {
        let _this = this//这里的_this指向的是vue的this
        _this.map = new amap.Map("dv-full-screen-container", {  //设置地图容器id
          zoom: 8,           //初始化地图级别
          mapStyle: 'amap://styles/darkblue',//amap://styles/e56d18683f6875dba8f7e63482f96c64，地图皮肤
          center: [105.602725, 37.076636], //初始化地图中心点位置
        });
        AMapUI.load(['ui/misc/PathSimplifier', 'lib/$'], function (PathSimplifier, $) {
          if (!PathSimplifier.supportCanvas) {
            alert('当前环境不支持 Canvas！');
            return;
          }
          _this.pathSimplifierIns = new PathSimplifier({
            zIndex: 100,//设置轨迹线的z-index
            //autoSetFitView:false,
            map: _this.map, //所属的地图实例

            getPath: function (pathData, pathIndex) {

              return pathData.path;
            },
            getHoverTitle: function (pathData, pathIndex, pointIndex) {

              if (pointIndex >= 0) {
                //point 
                return pathData.name + '，点：' + pointIndex + '/' + pathData.path.length;
              }

              return pathData.name + '，点数量' + pathData.path.length;
            },
            renderOptions: {

              renderAllPointsIfNumberBelow: 100 //绘制路线节点，如不需要可设置为-1
            }
          });

          window.pathSimplifierIns = _this.pathSimplifierIns;

          //设置数据
          _this.pathSimplifierIns.setData([{
            name: '路线0',
            path: [
              [116.405289, 39.904987],
              [113.964458, 40.54664],
              [111.47836, 41.135964],
              [108.949297, 41.670904],
              [106.380111, 42.149509],
              [103.774185, 42.56996],
              [101.135432, 42.930601],
              [98.46826, 43.229964],
              [95.777529, 43.466798],
              [93.068486, 43.64009],
              [90.34669, 43.749086],
              [87.61792, 43.793308]
            ]
          }]);

          //对第一条线路（即索引 0）创建一个巡航器
          var navg1 = _this.pathSimplifierIns.createPathNavigator(0, {
            loop: true, //循环播放
            speed: 1000000 //巡航速度，单位千米/小时
          });

          //navg1.start();
        });
      }).catch(err => {
        throw (new Error('加载高德地图失败：' + err,))
      })
    },
    initMapUi() {

    }
  },
}
</script>

<style lang="less" scoped>
#data-view {
  width: 100%;
  height: 100%;
  color: #fff;

  #dv-full-screen-container {
    width: 100%;
    height: 100%;
    box-shadow: 0 0 3px blue;
    display: flex;
    flex-direction: column;
  }

  .main-header {
    height: 80px;
    display: flex;
    justify-content: center;
    align-items: center;
    padding: 0 25%; //两边的间距
    z-index: 3;
    position: relative;

    .mh-middle {
      font-size: 30px;
    }

    .mh-right {
      position: absolute;
      right:30px;
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
    display: flex;
    justify-content: flex-end;

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

  .zindex {
    z-index: 2;
  }
}
</style>
