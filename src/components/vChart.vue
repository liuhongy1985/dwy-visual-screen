<template>
    <div :id="chartId"></div>
</template>

<script>
import * as echarts from 'echarts'

export default {
    name: 'vChart',
    data() {
        return {
            chart: null,
        }
    },
    props: {
        option: {
            type: Object,
            default: () => {
                return {}
            }
        },
        refValue: {
            type: String,
            default: ''
        }
    },
    watch: {
        option: {
            handler(val) {
                console.log(val)
                this.initChart()
            },
            deep: true
        }
    },
    computed: {
        chartId() {
            return `chart${Math.random() * 100000}`
        }
    },
    mounted() {
        let vm = this
        this.$nextTick(() => {
            vm.initChart()
        })
    },
    methods: {
        initChart() {
            this.chart = echarts.init(document.getElementById(this.chartId))
            // 监听窗口发生变化，resize组件
            window.addEventListener('resize', this.$_handleResizeChart)
            // 通过hook监听组件销毁钩子函数，并取消监听事件
            this.$once('hook:beforeDestroy', () => {
                window.removeEventListener('resize', this.$_handleResizeChart)
            })
            this.chart.setOption(this.option)
        },
        $_handleResizeChart() {
            this.chart.resize()
        },
    }
}
</script>

<style scoped>

</style>