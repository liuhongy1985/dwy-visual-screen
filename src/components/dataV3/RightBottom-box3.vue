<template>
    <div class="left-center">
        <box3_1></box3_1>
        <box3_2></box3_2>
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
    width: 26%;
    height: calc(100% - 50px);
    display: flex;
    flex-direction: column;
    justify-content: space-between;
}
</style>
