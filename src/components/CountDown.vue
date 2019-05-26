<template>
  <div class="countdown">
    <div v-if="finished" v-text="expiredText"></div>
    <div v-else>
      <span>{{ remaining.days}} Days</span><br>
      <span>{{ remaining.hours}} Hours</span><br>
      <span>{{ remaining.minutes}} Minutes</span><br>
      <span>{{ remaining.seconds}} Seconds</span><br>
    </div>
  </div>
</template>

<script>
import moment from 'moment'

export default {
  name: 'CountDown',
  props: {
    expiredText: {
      default: 'Now Expired'
    }
  },
  data () {
    return {
      now: new Date()
    }
  },
  created () {
    let interval = setInterval(() => {
      this.now = new Date()
    }, 1000)

    this.$on('finished', () => clearInterval(interval))
  },
  computed: {
    finished () {
      return false
    },
    remaining () {
      let remaining = moment.duration(moment('2019-12-12').diff(this.now))

      if (remaining <= 0) {
        this.$emit('finished')
      }

      return {
        days: remaining.days(),
        hours: remaining.hours(),
        minutes: remaining.minutes(),
        seconds: remaining.seconds()
      }
    }
  }
}
</script>
