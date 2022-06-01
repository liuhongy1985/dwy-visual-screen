<template>
    <div>
        <template v-for="(i, index) in formatter('00001234457')">
            <span class="M-Separator" v-if="i === ','">{{ i }}</span>
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
            if (i !== ',') {
                this.$refs[`flipper${index}`][0].flipDown(0, i)
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
        //千位分隔符
        formatter(number) {
            const numbers = number.toString().split('').reverse()
            const segs = []

            while (numbers.length) segs.push(numbers.splice(0, 3).join(''))

            return segs.join(',').split('').reverse().join('')
        },
    },
}
</script>
<style>
.M-Flipper {
    margin: 0 5px;
    width: 36px;
    height: 53px;
    line-height: 53px;
    font-size: 33px;
    background: linear-gradient(45deg, #ea553d, 50%, #fc9b71);
}

.M-Separator {
    margin: 0 5px;
    display: inline-block;
    position: relative;
    width: 36px;
    height: 53px;
    line-height: 53px;
    border-radius: 10px;
    background: linear-gradient(45deg, #ea553d, 50%, #fc9b71);
    font-size: 33px;
    color: #fff;
    box-shadow: 0 0 6px rgba(0, 0, 0, .5);
    text-align: center;
    font-family: "Helvetica Neue";
    vertical-align: top;
}
</style>