<template>
  <div class="home">
    <img alt="Vue logo" src="../assets/logo.png">
    <HelloWorld msg="https://laracasts.com/series/whatcha-working-on/episodes/25"/>
    <CountDown until="December 10 2019" expired-text="This site has launched!"></CountDown>
    <SelectizeSelect></SelectizeSelect>
    <SelectizeSelect></SelectizeSelect>
  </div>
</template>

<script>
// @ is an alias to /src
import HelloWorld from '@/components/HelloWorld.vue'
import CountDown from '@/components/CountDown.vue'
import SelectizeSelect from '@/components/Select.vue'

export default {
  name: 'home',
  props: {
    expiredText: {
      default: 'Now Expired'
    }
  },
  components: {
    HelloWorld,
    CountDown,
    SelectizeSelect
  }
}
</script>
<!-- Add "scoped" attribute to limit CSS to this component only -->
<style>
  .home {
    padding-bottom: 40px;
  }
</style>
