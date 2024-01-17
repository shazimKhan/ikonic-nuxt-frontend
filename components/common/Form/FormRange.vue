<template>
  <vue-slider
    v-model="currentValue"
    :class="[customSlider ? 'custom-slider' : '']"
    :variant="variant"
    :value="value"
    :dot-size="dotSize"
    :width="width"
    :height="height"
    :data="data"
    :data-value="dataValue"
    :data-label="dataLabel"
    :min="min"
    :max="max"
    :interval="interval"
    :tooltip="tooltip"
    :min-range="minRange"
    :max-range="maxRange"
    :marks="marks"
    :hide-label="hideLabel"
    :dot-style="dotStyle"
    :rail-style="railStyle"
    :process-style="processStyle"
    @change="$emit('change', currentValue)"
  />
</template>

<script>
import VueSlider from 'vue-slider-component'

export default {
  name: 'FormRange',
  components: { VueSlider },
  props: {
    variant: {
      type: String,
      default: '',
    },
    value: {
      type: [String, Number, Array],
      default: 0,
    },
    dotSize: {
      type: [Number, Array],
      default: 14,
    },
    width: {
      type: [Number, String],
      default: undefined,
    },
    height: {
      type: [Number, String],
      default: undefined,
    },
    data: {
      type: [Array, Object],
      default() {}
    },
    dataValue: {
      type: String,
      default: 'value',
    },
    dataLabel: {
      type: String,
      default: 'label',
    },
    min: {
      type: Number,
      default: 0,
    },
    max: {
      type: Number,
      default: 100,
    },
    interval: {
      type: Number,
      default: 1,
    },
    tooltip: {
      type: String,
      default: 'none',
      validator(tooltip) {
        return ['none', 'always', 'hover', 'focus', 'active'].includes(tooltip)
      }
    },
    range: {
      type: Array,
      default: null,
    },
    minRange: {
      type: Number,
      default: undefined,
    },
    maxRange: {
      type: Number,
      default: undefined,
    },
    marks: {
      type: [Boolean, Object, Function],
      default: undefined,
    },
    hideLabel: {
      type: Boolean,
      default: false,
    },
    dotStyle: {
      type: Object,
      default: null,
    },
    railStyle: {
      type: Object,
      default: null,
    },
    processStyle: {
      type: Object,
      default: null,
    },
    customSlider: {
      type: Boolean,
      default: false,
    },
  },
  data() {
    return {
      currentValue: this.range ?? null,
    }
  },
  watch: {
    range(newVal) {
      if (newVal) {
        this.currentValue = newVal
      }
    }
  }
}
</script>
