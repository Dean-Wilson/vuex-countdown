<template>
  <selectize v-model="selected" :settings="settings">
     <option :value="1">One</option>
     <option :value="2">Two</option>
  </selectize>
</template>
<script>
import Selectize from 'vue2-selectize'

export default {
  name: 'SelectizeSelect',
  components: {
    Selectize
  },
  data () {
    return {
      settings: {}, // https://github.com/selectize/selectize.js/blob/master/docs/usage.md
      selected: 1
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style>
  .selectize-control {
    margin-top: 20px;
  }
  .selectize-control input {
      /* min-width: 50px; */
  }
</style>
