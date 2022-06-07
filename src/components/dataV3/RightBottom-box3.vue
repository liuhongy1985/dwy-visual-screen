<template>
    <div class="left-center">
        <div class="lc-header"></div>
        <div class="lc-box4">
            <box3_1></box3_1>
        <box3_2></box3_2>
        </div>
    </div>
</template>

<script>
import box3_1 from './RightBottom-box3-1';
import box3_2 from './RightBottom-box3-2';

export default {
    name: 'LeftChart2',
    components: {
        box3_1,
        box3_2
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
        padding-top: 2px;
    }
}
</style>
