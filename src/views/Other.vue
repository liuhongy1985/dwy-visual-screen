<template>
    <div>
        <template v-for="(i, index) in formatNumber(1234457)">
            <span class="M-Separator" v-if="i===','">{{i}}</span>
            <Flop v-else :ref="'flipper' + index" />
        </template>
        <vueCountTo :startVal='0' :endVal='123123' :duration='3000'></vueCountTo>
    </div>
</template>
<script>
import Flop from '@/components/Flop.vue'
import vueCountTo from '@/components/vue-countTo'
export default {
    name: 'App',
    components: {
        Flop,
        vueCountTo
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
                this.$refs[`flipper${index}`][0].setFront(i)
            }
        });
        setTimeout(() => {
            this.run()
        }, 3000);
    },
    methods: {
        run() {
            let _this = this
            // 获取当前时间
            for (let i = 0; i < this.itemList.length; i++) {
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
    margin: 0 3px;
    font-size: 33px;
    text-align: center;
}
</style>