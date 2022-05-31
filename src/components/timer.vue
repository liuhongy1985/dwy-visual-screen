<template>
    <div class="timerBox">
        <p class="boxDay">{{ dateDay }}</p>
        <p class="boxDate">{{ dateWeek }}</p>
    </div>
</template>

<script>
import dayjs from 'dayjs'
export default {
    data() {
        return {
            timer: null,
            dateDay: '',
            dateYear: '',
            dateWeek: '',
            weekDay: ['星期日', '星期一', '星期二', '星期三', '星期四', '星期五', '星期六']
        }
    },
    mounted() {
        this.timer = setInterval(() => {
            this.dateDay = dayjs().format('YYYY-MM-DD HH:mm:ss')
            this.dateYear = dayjs().format('YYYY')
            this.dateWeek = this.weekDay[dayjs().day()]
        }, 1000)
    },
    beforeDestroy() {
        if (this.timer) {
            clearInterval(this.timer)
        }
    },
}
</script>

<style scoped>
.timerBox {
    color: #fff;
    display: flex;
    font-size: 20px;
    line-height: 1rem;
}
.boxDay {
    margin-right: 10px;
}
.boxDate {
    /* font-size: 16px; */
}
</style>

