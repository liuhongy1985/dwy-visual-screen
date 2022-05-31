<template>
    <div>
        <template v-for="(i, index) in formatNumber(1234457)">
            <span class="M-Separator" v-if="i===','">{{i}}</span>
            <Flop v-else :ref="'flipper' + index" />
        </template>
    </div>
</template>
<script>
import Flop from '@/components/Flop.vue'
export default {
    name: 'App',
    components: {
        Flop
    },
    data() {
        return {
            num: 1,
            timer: null,
            itemList: [1, 2, 3, 4, 5],
            flipperList: [],
            valueData: [1, 3, 4, 5, 6]
        }
    },
    mounted() {
        this.formatNumber(1234457).forEach((i, index) => {
            if (i!==',') {
                this.$refs[`flipper${index}`][0].flipDown(0,i)
            }
        });
    },
    methods: {
        run() {
            let _this = this
            // 获取当前时间
            for (let i = 0; i < this.formatNumber(3456734).length; i++) {
                if (this.itemList[i] === this.valueData[i]) {
                    continue
                }
                (function (t, data) {   // 注意这里是形参
                    setTimeout(function () {
                        _this.$refs[`flipper${i}`][0].flipDown(_this.itemList[i], _this.valueData[i])
                    }, 1000 * t);	// 还是每秒执行一次，不是累加的
                })(i, '其他参数')   // 注意这里是实参，这里把要用的参数传进去

            }
        },
        // 切换数字使用‘,’分割
        formatNumber(num) {
            num += '';
            const x = num.split('.');
            let x1 = x[0];
            const rgx = /(\d+)(\d{3})/;
            if (true) {
                while (rgx.test(x1)) {
                    x1 = x1.replace(rgx, '$1' + ',' + '$2');
                }
            }
            let a = '' + x1 + ''
            return [...a];
        }
    },
}
</script>
<style>
.M-Flipper {
    margin: 0 3px;
    width: 33px;
    height: 50px;
    line-height: 50px;
    font-size: 33px;
}
.M-Separator {
    display: inline-block;
    position: relative;
    width: 33px;
    height: 50px;
    line-height: 50px;
    border-radius: 10px;
    background: orangered;
    font-size: 33px;
    color: #fff;
    box-shadow: 0 0 6px rgba(0, 0, 0, .5);
    text-align: center;
    font-family: "Helvetica Neue";
    vertical-align: top;
}
</style>