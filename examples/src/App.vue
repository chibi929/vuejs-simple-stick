<template>
  <div id="app">
    <SimpleStick />
  </div>
</template>

<script lang="ts">
import Vue from 'vue'
import SimpleStick from '../../src/components/SimpleStick.vue'

export default Vue.extend({
  name: 'App',
  components: {
    SimpleStick,
  },
})
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
