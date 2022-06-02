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
                    name: '(%)',
                    nameTextStyle: {
                        fill: '#fff',
                        fontSize: 10
                    },
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
                        type: 'line',
                        lineStyle: {
                            stroke: '#fc9b71',
                        },
                        lineArea: {
                            show: true,
                            opacity: .1,
                            gradient: [ '#ea553d','#fc9b71']
                        },
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
