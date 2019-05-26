<template>
  <div class="home">
    <img alt="Vue logo" src="../assets/logo.png">
    <HelloWorld msg="https://laracasts.com/series/whatcha-working-on/episodes/25"/>
    <CountDown until="December 10 2019" expired-text="This site has launched!"></CountDown>
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
// @ is an alias to /src
import moment from 'moment'
import HelloWorld from '@/components/HelloWorld.vue'
import CountDown from '@/components/CountDown.vue'
import { setInterval, clearInterval } from 'timers'

export default {
  name: 'home',
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
  },
  components: {
    HelloWorld,
    CountDown
  }
}
</script>
