<template>
    <div class="right-center">
        <RightCenterBox1Vue></RightCenterBox1Vue>
        <div class="right-center-Box2">
            <small1></small1>
            <small2></small2>
        </div>
    </div>
</template>

<script>
import RightCenterBox1Vue from './RightCenter-box1.vue'
import small1 from './RightCenter-box-small1.vue'
import small2 from './RightCenter-box-small2.vue'
export default {
    name: 'RightCenter',
    components: {
        RightCenterBox1Vue,
        small1,
        small2
    },
    data() {
        return {

        }
    }
}
</script>

<style lang="less">
.right-center {
    width: 30%;
    height: 100%;
    display: flex;
    align-items: flex-end;

    .right-center-Box2 {
        margin-left: 2%;
        width: 48%;
        height: calc(100% - 50px);
        display: flex;
        flex-direction: column;
        justify-content: space-between;
    }
}
</style>
