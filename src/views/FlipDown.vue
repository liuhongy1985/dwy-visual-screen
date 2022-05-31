<template>
    <div class="flip down" ref="flip">
            <!-- 位于前面的纸牌 -->
            <div class="digital front number0" ref="frontNode"></div>
            <!-- 位于后面的纸牌 -->
            <div class="digital back number1" ref="backNode"></div>
        </div>
</template>
<script>
export default {
    name: 'App',
    components: {
    },
    data() {
        return {
            flip: null,
            backNode: null,
            frontNode: null,
            count: 0,// 当前数字
            isFlipping: false,// 是否正在翻转（防止翻转未结束就进行下一次翻转）
        }
    },
    mounted() {
        this.$nextTick(() => {
            this.flip = this.$refs.flip;
            this.backNode = this.$refs.backNode;
            this.frontNode = this.$refs.frontNode;
        })
    },
    methods: {
        flipDown() {
            // 如果处于翻转中，则不执行
            if (this.isFlipping) {
                return false
            }
            // 设置前牌的文字
            this.frontNode.setAttribute('class', 'digital front number' + this.count)
            // 计算后牌文字（越界判断）
            let nextCount = this.count >= 9 ? 0 : (this.count + 1)
            // 设置后牌的文字
            this.backNode.setAttribute('class', 'digital back number' + nextCount)
            // 添加go，执行翻转动画
            this.flip.setAttribute('class', 'flip down go')
            // 将翻转态设置为true
            this.isFlipping = true
            // 翻转结束后，恢复状态
            setTimeout(() => {
                // 去掉go
                this.flip.setAttribute('class', 'flip down')
                // 将翻转态设置为false
                this.isFlipping = false
                // 设置前牌文字为+1后的数字
                this.frontNode.setAttribute('class', 'digital front number' + nextCount)
                // 更新当前文字
                this.count = nextCount
            }, 1000)
        },
        // 向上翻转-1（同理，注释略）
        flipUp() {
            if (this.isFlipping) {
                return false
            }
            this.frontNode.setAttribute('class', 'digital front number' + this.count)
            let nextCount = this.count <= 0 ? 9 : (this.count - 1)
            this.backNode.setAttribute('class', 'digital back number' + nextCount)
            this.flip.setAttribute('class', 'flip up go')
            this.isFlipping = true
            setTimeout(() => {
                this.flip.setAttribute('class', 'flip up')
                this.isFlipping = false
                this.frontNode.setAttribute('class', 'digital front number' + nextCount)
                this.count = nextCount
            }, 1000)
        }
    },
}
</script>
<style lang="less">
.flip {
    display: inline-block;
    position: relative;
    width: 60px;
    height: 100px;
    line-height: 100px;
    border: solid 1px #000;
    border-radius: 10px;
    background: #fff;
    font-size: 66px;
    color: #fff;
    box-shadow: 0 0 6px rgba(0, 0, 0, .5);
    text-align: center;
    font-family: "Helvetica Neue";
}

.flip .digital:before,
.flip .digital:after {
    content: "";
    position: absolute;
    left: 0;
    right: 0;
    background: #000;
    overflow: hidden;
    box-sizing: border-box;
}

.flip .digital:before {
    top: 0;
    bottom: 50%;
    border-radius: 10px 10px 0 0;
    border-bottom: solid 1px #666;
}

.flip .digital:after {
    top: 50%;
    bottom: 0;
    border-radius: 0 0 10px 10px;
    line-height: 0;
}

.flip .number0:before,
.flip .number0:after {
    content: "0";
}

.flip .number1:before,
.flip .number1:after {
    content: "1";
}

.flip .number2:before,
.flip .number2:after {
    content: "2";
}

.flip .number3:before,
.flip .number3:after {
    content: "3";
}

.flip .number4:before,
.flip .number4:after {
    content: "4";
}

.flip .number5:before,
.flip .number5:after {
    content: "5";
}

.flip .number6:before,
.flip .number6:after {
    content: "6";
}

.flip .number7:before,
.flip .number7:after {
    content: "7";
}

.flip .number8:before,
.flip .number8:after {
    content: "8";
}

.flip .number9:before,
.flip .number9:after {
    content: "9";
}

/*向下翻*/
.flip.down .front:before {
    z-index: 3;
}

.flip.down .back:after {
    z-index: 2;
    transform-origin: 50% 0%;
    transform: perspective(160px) rotateX(180deg);
}

.flip.down .front:after,
.flip.down .back:before {
    z-index: 1;
}

/*向上翻*/
.flip.up .front:after {
    z-index: 3;
}

.flip.up .back:before {
    z-index: 2;
    transform-origin: 50% 100%;
    transform: perspective(160px) rotateX(-180deg);
}

.flip.up .front:before,
.flip.up .back:after {
    z-index: 1;
}

//向下翻-动画
.flip.down.go .front:before {
    transform-origin: 50% 100%;
    animation: frontFlipDown 0.6s ease-in-out both;
    box-shadow: 0 -2px 6px rgba(255, 255, 255, 0.3);
    backface-visibility: hidden;
}

.flip.down.go .back:after {
    animation: backFlipDown 0.6s ease-in-out both;
}

@keyframes frontFlipDown {
    0% {
        transform: perspective(160px) rotateX(0deg);
    }

    100% {
        transform: perspective(160px) rotateX(-180deg);
    }
}

@keyframes backFlipDown {
    0% {
        transform: perspective(160px) rotateX(180deg);
    }

    100% {
        transform: perspective(160px) rotateX(0deg);
    }
}

.flip.up.go .front:after {
    transform-origin: 50% 0;
    animation: frontFlipUp 0.6s ease-in-out both;
    box-shadow: 0 2px 6px rgba(255, 255, 255, 0.3);
    backface-visibility: hidden;
}

// 向上翻-动画
.flip.up.go .back:before {
    animation: backFlipUp 0.6s ease-in-out both;
}

@keyframes frontFlipUp {
    0% {
        transform: perspective(160px) rotateX(0deg);
    }

    100% {
        transform: perspective(160px) rotateX(180deg);
    }
}

@keyframes backFlipUp {
    0% {
        transform: perspective(160px) rotateX(-180deg);
    }

    100% {
        transform: perspective(160px) rotateX(0deg);
    }
}
</style>