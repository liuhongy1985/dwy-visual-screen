<template>
  <ul class="flex">
    <ScrollNum
      v-for="(number, idx) of numArr"
      :key="idx"
      :i="number"
      :delay="idx + 2.5"
      as="li"
      class="num"
    />
  </ul>
</template>

<script>
import ScrollNum from './ScrollNum.vue'

export default {
  name: 'Flipper',
  components: { ScrollNum },
  data: () => ({ num: 886 }),
  computed: {
    numArr () {
      const str = String(this.num)
      let arr = []

      for (let i = 0; i < str.length; i++) {
        arr.push(parseInt(str[i]))
      }
      
      return arr
    }
  },
  mounted () {
    setInterval(() => this.num++, 10000)
  },
  beforeDestroy() {
  },
}
</script>

<style>
.flex {
  display: flex;
  margin: 0 10px;
}
ul {
  padding: 0;
  margin: 0;
  list-style: none;
}
.num {
  --width: 36px;
  margin-right: 6px;
  border: 1px solid #08e5ff;
  background-color: rgba(4, 49, 128, 0.6);
  /* border-radius: 8px */
}
</style>

