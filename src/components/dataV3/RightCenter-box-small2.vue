<template>
    <div class="right-center">
        <dv-border-box-7 class="rc-header-box" :color="['#0069b3', '#20d6d9']">
            <div class="rc-details">
                <span class="rc-details-before"></span>
                <span class="rc-details-span">投保情况</span>
                <span class="rc-details-after"></span>
                <dv-charts class="rc-chart" :option="option" />
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
                series: [
                    {
                        type: 'gauge',
                        startAngle: -Math.PI / 2,
                        endAngle: Math.PI * 1.5,
                        arcLineWidth: 10,
                        radius:45,
                        data: [
                            { name: 'itemA', value: 65, gradient: ['#c1f634', '#61e498', '#07d1f7'] ,lineWidth:10,localGradient :true}
                        ],
                        axisLabel: {
                            show: false
                        },
                        axisTick: {
                            show: false
                        },
                        pointer: {
                            show: false
                        },
                        dataItemStyle: {
                            lineCap: 'round'
                        },
                        details: {
                            show: true,
                            formatter: '{value}%',
                            style: {
                                fill: '#1ed3e5',
                                fontSize: 20
                            }
                        }
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
