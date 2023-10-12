<template>
  <div id="app" class="red">
    <div class="box blue">
      <SimpleStick class="green" title="left" @input="onInput1" />
    </div>
    <div class="box blue"></div>
    <div class="box blue">
      <SimpleStick class="green" title="right" @input="onInput2" />
    </div>
  </div>
</template>

<script lang="ts">
import Vue from 'vue'
import SimpleStick from '../../src/components/SimpleStick.vue'
import type { ISimpleStickStatus } from '../../src/types'

export default Vue.extend({
  name: 'App',
  components: {
    SimpleStick,
  },
  methods: {
    onInput1(status: ISimpleStickStatus) {
      console.log('onInput1:', status)
    },
    onInput2(status: ISimpleStickStatus) {
      console.log('onInput2:', status)
    },
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

  display: flex;
  justify-content: center;
  align-items: center;
}
.box {
  width: 300px;
  height: 300px;
  margin: 1em;

  display: flex;
  justify-content: center;
  align-items: center;
}
.red {
  background-color: #ffcccc;
}
.green {
  background-color: #ccffcc;
}
.blue {
  background-color: #ccccff;
}
</style>
