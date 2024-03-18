<script>
export default {
  data() {
    return {
      time: 'time',
      date: 'date',
      weekday: 'weekday'
    }
  },
  created() {
    this.date = this.getDate()
    this.time = this.updateTime()
    this.weekday = this.getWeekday()
  },
  mounted() {
    this.interval = setInterval(() => {
      this.time = this.updateTime()
    }, 1000)
  },
  methods: {
    getDate() {
      let date = new Date()
      return date.getDate() + '.' + date.getUTCMonth() + '.' + date.getFullYear()
    },
    updateTime() {
      let date = new Date()
      return date.getHours() + ':' + date.getMinutes() + ':' + date.getSeconds()
    },
    getWeekday() {
      let date = new Date()

      switch (date.getDay()) {
        case 1:
          return 'Monday'
        case 2:
          return 'Tuesday'
        case 3:
          return 'Wednesday'
        case 4:
          return 'Thursday'
        case 5:
          return 'Friday'
        case 6:
          return 'Saturday'
        case 7:
          return 'Sunday'
      }
    }
  }
}
</script>

<template>
  <h2>It is {{ weekday }}, the {{ date }}</h2>
  <h2>{{ time }}</h2>
</template>
