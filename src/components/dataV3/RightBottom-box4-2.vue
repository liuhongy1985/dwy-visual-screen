<template>
    <div class="right-center">
        <dv-border-box-7 class="rc-header-box" :color="['#0069b3', '#20d6d9']">
            <div class="rc-details">
                <span class="rc-details-before"></span>
                <span class="rc-details-span">注册用户人数占比情况</span>
                <span class="rc-details-after"></span>
                <!-- <dv-charts class="rc-chart" :option="option" /> -->
                <v-chart :refValue="'carNoChart'" class='rc-chart' :option='option' />
            </div>
        </dv-border-box-7>
    </div>
</template>

<script>
import vChart from '../vChart.vue'
export default {
    name: 'LeftChart2',
    components: {
        vChart,
    },
    data() {
        return {
            option: {
                grid: {
                    left: '5%',
                    containLabel: true
                },
                color: ['#0069b3', '#20d6d9', '#c1f634'],
                legend: {
                    show: true,
                    orient: 'vertical',
                    right: '5%',
                    top: 'center',
                    textStyle: {
                        color: '#fff',
                    },
                    formatter: (params) => {  //格式化数据的函数
                        console.log('我的参数', params)  //打印出来的数据（营业，网络，房屋，tgtn,g）
                        let arr = this.option.series[0].data
                        for (let a = 0; a < arr.length; a++) {
                            if (arr[a].name == params) {   //两个名称进行对比，取出对应的次数
                                return params + '   ' + arr[a].value  //然后return你需要的legend格式即可
                            }
                        }
                    },
                },
                label: {
                    formatter: '{a|{b}:{d}%}',
                    borderWidth: 1,
                    borderRadius: 4,
                    color: '#fff',
                    fontFamily: 'PingFangSC-Regular',
                    fontSize: '12px',
                    rich: {
                        a: {
                            color: '#fff',
                            lineHeight: 10,
                            align: 'center'
                        }
                    }
                },
                series: [
                    {
                        type: 'pie',
                        data: [
                            { name: '货主', value: 93 },
                            { name: '承运商', value: 32 },
                            { name: '司机', value: 65 },
                        ],
                        radius: ['40%', '50%'],
                        center: ['30%','50%'],//调整图片位子
                        insideLabel: {
                            show: true
                        },
                        outsideLabel: {
                            labelLineEndLength: 11,
                        },
                    }
                ]
            }
        }
    }
}
</script>

<style lang="less" scoped>
.right-center {
    width: 100%;
    height: 49%;
    display: flex;

    .rc-header-box {

        .rc-details-before {
            display: inline-block;
            width: 10px;
            height: 10px;
            background-size: 100% 100%;
            background-repeat: no-repeat;
            background-image: url(./img/before.png);
            margin-right: 5px;
        }

        .rc-details-after {
            display: inline-block;
            width: 30%;
            height: 10px;
            background-image: url(./img/after.png);
            background-size: 100% 100%;
            background-repeat: no-repeat;
            margin-left: 10px;
        }

        .rc-details {
            height: 100%;
            width: 100%;
            padding: 20px;

            .rc-chart {
                height: calc(~"100% - 40px");
                width: 100%;
            }
        }
    }
}
</style>
