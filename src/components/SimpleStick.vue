<template>
  <div id="joystick" class="simple-stick" :style="styles"></div>
</template>

<script>
import JoyStick from '../joystick'

export default {
  name: 'SimpleStick',
  props: {
    title: { type: String, default: undefined },
    width: { type: Number, default: 200 },
    height: { type: Number, default: 200 },
    internalFillColor: { type: String, default: undefined },
    internalLineWidth: { type: Number, default: undefined },
    internalStrokeColor: { type: String, default: undefined },
    externalLineWidth: { type: Number, default: undefined },
    externalStrokeColor: { type: String, default: undefined },
    autoReturnToCenter: { type: Boolean, default: undefined },
  },
  data() {
    return {
      joy: undefined,
      direction: 'C',
      continuousIntervalId: null,
      continuousCount: 0,
    }
  },
  computed: {
    styles() {
      return {
        '--stick-width': `${this.width}px`,
        '--stick-height': `${this.height}px`,
      }
    },
    joyParams() {
      return {
        title: this.title,
        width: this.width,
        height: this.height,
        internalFillColor: this.internalFillColor,
        internalLineWidth: this.internalLineWidth,
        internalStrokeColor: this.internalStrokeColor,
        externalLineWidth: this.externalLineWidth,
        externalStrokeColor: this.externalStrokeColor,
        autoReturnToCenter: this.autoReturnToCenter,
      }
    },
  },
  mounted() {
    this.joy = new JoyStick('joystick', this.joyParams, (stickStatus) => {
      const { cardinalDirection } = stickStatus
      if (this.direction === cardinalDirection) {
        return
      }

      this.direction = cardinalDirection
      if (this.direction === 'C') {
        this.clearContinuousJoy()
      } else {
        this.continuousJoy()
      }
    })
  },
  methods: {
    continuousJoy() {
      this.clearContinuousJoy()
      this.continuousIntervalId = setInterval(() => {
        ++this.continuousCount
        this.$emit('input', {
          direction: this.direction,
          count: this.continuousCount,
        })
      }, 1000 / 10)
      this.$emit('input', {
        direction: this.direction,
        count: this.continuousCount,
      })
    },
    clearContinuousJoy() {
      this.continuousCount = 0
      if (this.continuousIntervalId != null) {
        clearInterval(this.continuousIntervalId)
        this.continuousIntervalId = null
      }
    },
  },
}
</script>

<style scoped>
.simple-stick {
  position: relative;
  width: var(--stick-width, '200px');
  height: var(--stick-height, '200px');
}
.simple-stick #joystick {
  position: absolute;
  top: 0;
  height: 0;
}
</style>
