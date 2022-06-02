<template>
    <div class="right-center">
        <dv-border-box-7 class="rc-header-box" :color="['#0069b3', '#20d6d9']">
            <div class="rc-details">
                <span class="rc-details-before"></span>
                <span class="rc-details-span">本月新增车辆情况</span>
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
                legend: {
                    data: ['车辆总数', '运输中总量', '使用率'],
                    top: 20,
                    right: 100,
                    //type: 'scroll',
                    //orient: 'vertical',
                    textStyle: {
                        fontSize: 12,
                        fill: '#fff'
                    }
                },
                xAxis: {
                    data: [
                        '周一', '周二', '周三', '周四', '周五', '周六', '周日'
                    ],
                    axisLabel: {
                        style: {
                            rotate: 20,
                            textAlign: 'left',
                            textBaseline: 'top',
                            fill: '#20d6d9',
                        }
                    },
                    axisTick: {
                        show: false
                    }
                },
                yAxis: [
                    {
                        name: '(辆)',
                        nameTextStyle: {
                            fill: '#fff',
                            fontSize: 10,
                            padding: [0, 0, 0, 30]
                        },
                        data: 'value',
                        min: 0,
                        max: 300,
                        interval: 50,
                        splitLine: {
                            show: false,
                            style: {
                                fill: '#20d6d9',
                                lineDash: [3, 3]
                            }
                        },
                        axisLabel: {
                            style: {
                                fill: '#20d6d9',
                            },
                            formatter: '{value} ml'
                        },
                        axisTick: {
                            show: false
                        }
                    },
                    {
                        name: '(%)',
                        nameTextStyle: {
                            fill: '#fff',
                            fontSize: 10,
                        },
                        data: 'value',
                        position: 'right',
                        min: 0,
                        max: 30,
                        interval: 5,
                        splitLine: {
                            fill: '#20d6d9',
                            show: false
                        },
                        axisLabel: {
                            style: {
                                fill: '#20d6d9',
                            },
                            formatter: '{value} °C',
                        },
                        axisTick: {
                            show: false
                        }
                    }
                ],
                series: [
                    {
                        name: '车辆总数',
                        data: [
                            175, 125, 90, 130, 45, 65,
                            65
                        ],
                        type: 'bar',
                        gradient: {
                            color: ['#20d6d9', '#20d6d9']
                        },
                        animationCurve: 'easeOutBounce'
                    },
                    {
                        name: '运输中总量',
                        data: [
                            175, 125, 90, 130, 45, 65,
                            65
                        ],
                        type: 'bar',
                        gradient: {
                            color: ['#37a2da', '#67e0e3']
                        },
                        animationCurve: 'easeOutBounce'
                    },
                    {
                        name: '使用率',
                        data: [
                            23, 18, 16, 14, 10, 8,
                            6
                        ],
                        type: 'line',
                        lineStyle: {
                            stroke: '#fc9b71',
                        },
                        yAxisIndex: 1,
                        animationCurve: 'easeOutBounce'
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
                width: 90%;
            }
        }
    }
}
</style>
