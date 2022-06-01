<template>
    <div class="left-center">
        
    </div>
</template>

<script>
export default {
    name: 'LeftChart2',
    data() {
        return {
            option: {
                grid: {
                    left: '25%',
                    right: '4%',
                    containLabel: true
                },
                xAxis: {
                    data: 'value',
                    axisLabel: {
                        style: {
                            fill: '#0069b3',
                        }
                    }
                },
                yAxis: {
                    axisLabel: {
                        interval: 0,
                        style: {
                            fill: '#fff',
                        }
                    },
                    splitLine: {
                        show: false,
                    },
                    data: ['厦门达达', '厦门达达股份有限公司', '厦门达达股份有限公司', '厦门达达股份有限公司', '厦门达达股份有限公司', '厦门达达股份有限公司', '厦门达达股份有限公司', '厦门达达股份有限公司', '厦门达达111']
                },
                series: [
                    {
                        
                        data: [1200, 2230, 1900, 2100, 3500, 4200, 3985, 4999, 7999],
                        gradient: {
                            color: [ '#ea553d','#fc9b71']
                        },
                        type: 'bar',
                        animationCurve: 'easeOutBack',
                        label: {
                            show: true,
                            position: 'right',
                            offset: [20, 0],
                            style: {
                                fill: '#fff'
                            }
                        },
                    }
                ]
            }
        }
    }
}
</script>

<style lang="less" scoped>
.left-center {
    width: 27%;
    height: 100%;
    background-color: #fff;
}
</style>
