<template>
    <div class="right-center">
        <RightCenterBox1Vue></RightCenterBox1Vue>
    </div>
</template>

<script>
import RightCenterBox1Vue from './RightCenter-box1.vue'
export default {
    name: 'RightCenter',
    components: {
        RightCenterBox1Vue
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
}
</style>
