<template>
  <div class="center-box">
    <span class="center-tittle">交易量</span>
    <div class="center-flop">
      <FlopVue></FlopVue>
    </div>
    <div class="center-num">
      <div class="center-num-tittle">
        <span>
          订单总量
        </span>
        <dv-digital-flop :config="config1" style="width:300px;height:45px;text-align: start;
" />
      </div>
      <div class="center-num-tittle">
        <span>
          运单总量
        </span>
        <dv-digital-flop :config="config1" style="width:300px;height:45px;text-align: start;
" />
      </div>
    </div>
    <div class="center-bottom">
      <span>
        运输总量
      </span>
      <dv-digital-flop :config="config3" class="center-bottom-flop" />
    </div>
  </div>
</template>

<script>
import FlopVue from './FilpPackage.vue'
function formatter(number) {
  const numbers = number.toString().split('').reverse()
  const segs = []

  while (numbers.length) segs.push(numbers.splice(0, 3).join(''))

  return segs.join(',').split('').reverse().join('')
}
export default {
  components: {
    FlopVue,
  },
  data() {
    return {
      config1: {
        number: [10222220],
        content: '{nt}笔',
        formatter,
        style: {
          fontSize: 40,
          fill: '#fff',
          textAlign: 'start'
        }
      },
      config3: {
        number: [10222220],
        content: '{nt}吨',
        formatter,
        style: {
          fontSize: 40,
          fill: '#fff',
          textAlign: 'start'
        }
      }
    }
  },
}
</script>

<style lang="less">
.center-box {
  width: 40%;
  height: calc(~"100% - 50px");
  margin-top: 50px;
  background-image: url(./img/center.png);
  background-size: 100% 100%;
  background-repeat: no-repeat;
  background-clip: content-box;

  display: flex;
  flex-direction: column;
  align-items: center;

  .center-tittle {
    font-size: 30px;
    text-align: center;
  }

  .center-flop {
    margin-top: 5px;
  }

  .center-num {
    font-size: 30px;
    display: flex;
    justify-content: space-between;

    &-tittle {
      margin-top: 10px;
      text-align: center;
    }
  }

  .center-bottom {
    font-size: 30px;
    text-align: center;
    margin-top: 20px;

    span {
      display: inline-block;
      margin-bottom: 10px;
    }

     &-flop {
      width: 300px;
      height: 55px;
      text-align: start;
      background: linear-gradient(45deg, #ea553d, 50%, #fc9b71);
      border-radius: 10px;
    }
  }
}
</style>
