<template>
  <div class="center-cmp">
    <dv-flyline-chart-enhanced :config="config" :dev="true" style="width:100%;height:100%;" />
  </div>
</template>

<script>
import LabelTag from './LabelTag'

export default {
  name: 'CenterCmp',
  components: {
    LabelTag
  },
  data() {
    return {
      config: {
        points: [
          {
            name: '南平市',
            coordinate: [0.52, 0.20],
            icon: {
              show: true,
              src: require('./img/mapPoint.png'),
              with: 30,
              height: 30
            },
            halo: {
              show: true
            },
            text: {
              color: '#fb7293'
            }
          },
          {
            name: '宁德市',
            coordinate: [0.82, 0.27]
          },
          {
            name: '三明市',
            coordinate: [0.36, 0.43]
          },
          {
            name: '福州市',
            coordinate: [0.69, 0.46]
          },
          {
            name: '莆田',
            coordinate: [0.65, 0.60]
          },
          {
            name: '泉州',
            coordinate: [0.51, 0.64]
          },
          {
            name: '厦门',
            halo: {
              show: true,
              color: '#37a2da'
            },
            coordinate: [0.48, 0.76]
          },
          {
            name: '漳州',
            coordinate: [0.33, 0.82]
          },
          {
            name: '龙岩市',
            coordinate: [0.17, 0.63]
          },
        ],
        lines: [
          {
            source: '南平市',
            target: '泉州'
          },
          {
            source: '南平市',
            target: '宁德市'
          },
          {
            source: '泉州',
            target: '莆田'
          },
          {
            source: '南平市',
            target: '龙岩市'
          },
          {
            source: '南平市',
            target: '泉州'
          },
          {
            source: '南平市',
            target: '福州市'
          },
          {
            source: '厦门',
            target: '福州市',
            color: '#8378ea'
          },
          {
            source: '厦门',
            target: '漳州',
            color: '#8378ea'
          },
          {
            source: '厦门',
            target: '三明市',
            color: '#8378ea',
            width: 13
          },
          {
            source: '厦门',
            target: '南平市',
            color: '#8378ea'
          },
          {
            source: '厦门',
            target: '龙岩市',
            color: '#8378ea'
          },
        ],
        icon: {
          show: true,
          src: require('./img/mapPoint.png'),
        },
        text: {
          show: true,
        },
        bgImgSrc: require('./img/center-cmp.png')
      }
    }
  }
}
</script>

<style lang="less">
.center-cmp {
  width: 100%;
  height: 100%;
  margin: 0px;
  padding: 0px;
  display: flex;
  flex-direction: column;
}
</style>
