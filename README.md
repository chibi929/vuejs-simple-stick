# vuejs-simple-stick

This is a Vue.js(v2.x+) component.  
[JoyStick](https://github.com/bobboteck/JoyStick) wrapped for Vue.js(v2.x+). Thank you!

## Usage

Register the locally within components.

```ts
import SimpleStick from 'vuejs-simple-stick'

export default {
  components: {
    SimpleStick
  }
}
```

Or globally using `Vue.compoennt`

```ts
import Vue from 'vue'
import SimpleStick from 'vuejs-simple-stick'

Vue.component('SimpleStick', SimpleStick)
```

### Example

```html
<template>
  <VuejsSimpleStick @input="onInput" />
</template>

<script>
export defualt {
  methods: {
    onInput(value) {
      console.log('onInput:', value)
    }
  }
}
</script>
```
