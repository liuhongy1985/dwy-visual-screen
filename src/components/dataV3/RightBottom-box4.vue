<template>
    <div class="left-center">
        <div class="lc-header">用户注册情况分析</div>
        <div class="lc-box4">
            <box4_1></box4_1>
            <box4_2></box4_2>
        </div>
    </div>
</template>

<script>
import box4_1 from './RightBottom-box4-1.vue'
import box4_2 from './RightBottom-box4-2.vue'

export default {
    name: 'LeftChart2',
    components: {
        box4_1,
        box4_2,
    },
    data() {
        return {
        }
    }
}
</script>

<style lang="less" scoped>
.left-center {
    width: 27%;
    height: 100%;

    .lc-box4 {
        width: 100%;
        height: calc(100% - 50px);
        display: flex;
        flex-direction: column;
        justify-content: space-between;
    }
}
</style>
