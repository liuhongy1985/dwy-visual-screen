<template>
    <div class="right-center">
        <div class="rc-header">派单运抵情况</div>
        <dv-border-box-7 class="rc-header-box" :color="['#0069b3', '#20d6d9']">
            <div class="rc-details">
                <span class="rc-details-before"></span>
                <span class="rc-details-span">运单送达情况</span>
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
                        splitNum: 11,
                        data: [
                            { name: 'itemA', value: 90, gradient: ['#e7bcf3', '#e690d1', '#fb7293'] }
                        ],
                        axisLabel: {
                            formatter: '{value}%',
                        },
                        axisTick: {
                            style: {
                                stroke: '#20d6d9',
                            }
                        },
                        axisLabel: {
                            style: {
                                stroke: '#20d6d9',
                            }
                        },
                        pointer: {
                            style: {
                                fill: '#20d6d9',
                            }
                        },
                        details: {
                            show: true,
                            offset: [0, 80],
                            formatter: '{value}%',
                            style: {
                                fontSize: 20,
                                color: '#20d6d9',
                            }
                        },
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
    width: 50%;
    height: 100%;

    .rc-header {
        height: 50px;
        line-height: 50px;
        font-weight: bold;
        font-size: 20px;
        color: #fff;
    }

    .rc-header-box {
        height: calc(~"100% - 50px");
        width: 100%;

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
                height: calc(~"100% - 70px");
                width: 90%;
            }
        }
    }
}
</style>
