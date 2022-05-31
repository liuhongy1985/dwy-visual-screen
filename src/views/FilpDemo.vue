<template>
    <div>
        <template v-for="(i, index) in formatNumber(1234457)">
            <span class="M-Separator" v-if="i===','">{{i}}</span>
            <FlipDown v-else :ref="'flipper' + index" />
        </template>
    </div>
</template>
<script>
import FlipDown from './FlipDown.vue'
export default {
    name: 'App',
    components: {
        FlipDown
    },
    data() {
        return {
            
        }
    },
    mounted() {
        
    },
    methods: {
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
.flip {
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
    height: 52px;
    line-height: 52px;
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