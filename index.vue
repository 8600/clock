<template>
  <div>{{time}}</div>
</template>

<script>
  export default {
    data () {
      return {
        time: '',
        clock: null
      }
    },
    mounted () {
      function checkTmie(num) {
        return num < 10 ? '0' + num : num
      }
      this.clock = setInterval(() => {
        const myDate = new Date()
        this.time = checkTmie(myDate.getHours()) + ':' + checkTmie(myDate.getMinutes()) + ':' + checkTmie(myDate.getSeconds())
      }, 1000)
    },
    beforeDestroy () {
      // 清除定时器
      window.clearInterval(this.clock)
    }
  }
</script>