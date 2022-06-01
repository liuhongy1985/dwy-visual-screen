<template>
  <div class="left-center">
    <div class="lc-header">货主订单月报</div>
    <dv-border-box-7 class="lc-header-box" :color="['#0069b3', '#20d6d9']">

      <div class="lc-details">
        <span class="lc-details-before"></span>
        <span class="lc-details-span">本月货主下单情况</span>
        <span class="lc-details-after"></span>
        <dv-charts class="lc-chart" :option="option" />
      </div>
    </dv-border-box-7>
  </div>
</template>

<script>
export default {
  name: 'LeftChart2',
  data() {
    return {
      option: {
        xAxis: {
          data: ['周一', '周二', '周三', '周四'],
          axisLine: {
            style: {
              stroke: '#fff',
            },
          },
          axisTick: {
            style: {
              stroke: '#fff',
            },
          },
          axisLabel: {
            style: {
              fill: '#20d6d9',
            },
          },
        },
        yAxis: {
          data: 'value',
          axisLine: {
            style: {
              stroke: '#fff',
            },
          },
          axisTick: {
            style: {
              stroke: '#fff',
            },
          },
          axisLabel: {
            style: {
              fill: '#20d6d9',
            },
          },
          splitLine: {
            show: false,
            style: {
              stroke: '#fff',
            },
          },
        },
        series: [
          {
            data: [1200, 2230, 1900, 2100],
            type: 'bar',
            barWidth: 20,
            label: {
              show: true,
              position: 'top',
              offset: [0, -10],
              style: {
                fill: '#fff'
              }
            },
          }
        ],
        color: ['#00baff', '#3de7c9', '#fff', '#ffc530', '#469f4b'],
      }
    }
  }
}
</script>

<style lang="less">
.left-center {
  width: 30%;
  height: 100%;

  .lc-header {
    height: 50px;
    line-height: 50px;
    font-weight: bold;
    font-size: 20px;
    color: #fff;
  }

  .lc-header-box {
    height: calc(~"100% - 50px");

    .lc-details-before {
      display: inline-block;
      width: 10px;
      height: 10px;
      background-size: 100% 100%;
      background-repeat: no-repeat;
      background-image: url(./img/before.png);
      margin-right: 5px;
    }
    .lc-details-after {
      display: inline-block;
      width: 30%;
      height: 10px;
      background-image: url(./img/after.png);
      background-size: 100% 100%;
      background-repeat: no-repeat;
      margin-left: 10px;
    }
    .lc-details {
      height: 100%;
      width: 100%;
      padding: 20px;
      .lc-chart {
        height: calc(~"100% - 70px");
        width: 90%;
      }
    }
  }
}
</style>
