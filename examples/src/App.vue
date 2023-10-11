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
body {
  margin: 0;
  padding: 0;
}
#app {
  position: fixed;
  width: 100%;
  height: 100%;
  background-color: #ffcccc;

  display: flex;
  justify-content: center;
  align-items: center;
}
</style>
