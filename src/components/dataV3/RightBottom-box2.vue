<template>
    <div class="left-center">
        <dv-border-box-7 class="rc-header-box" :color="['#0069b3', '#20d6d9']">
            <div class="lc-details">
                <span class="lc-details-before"></span>
                <span class="lc-details-span">本月货主下单情况</span>
                <dv-charts class="lc-chart" :option="option" />
                <div class="lc-details-title">
                    <div class="title-box">
                        <span>车辆数</span>123,123
                    </div>
                    <div class="title-box">
                        <span>GPS入网</span>123,123
                    </div>
                </div>
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
                        startAngle: -Math.PI / .8,
                        endAngle: Math.PI * 1.1,
                        arcLineWidth: 10,
                        radius: 100,
                        data: [
                            { name: 'itemA', value: 63, gradient: ['#f845f8', '#205ae2'], lineWidth: 10, localGradient: true }
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
                        backgroundArc: {
                            show: false
                        },
                        
                        details: {
                            show: true,
                            text: "拒付分析",
                            formatter: '{value}%'+'\n'+'GPS入网率',
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
.left-center {
    width: 15%;
    height: calc(100% - 50px);

    .rc-header-box {
        height: 100%;
        width: 100%;

        .lc-details-before {
            display: inline-block;
            width: 10px;
            height: 10px;
            background-size: 100% 100%;
            background-repeat: no-repeat;
            background-image: url(./img/before.png);
            margin-right: 5px;
        }

        .lc-details {
            height: 100%;
            width: 100%;
            padding: 20px;

            .lc-chart {
                height: 50%;
                width: 90%;
                margin: 20px 0;
            }

            .lc-details-title {
                display: flex;
                flex-direction: column;
                justify-content: center;
                align-items: center;
                font-size: 20px;
                margin-left: -30px;
                .title-box >span{
                    display:inline-block;
                    width: 100px;
                    line-height: 30px;
                    background-color: #205ae2;
                    color: #20d6d9;
                    text-align: center;
                    margin-bottom: 10px;
                    margin-right: 10px;
                }
            }
        }
    }
}
</style>
