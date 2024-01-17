<template>
  <b-form-checkbox
    v-model="localValue"
    :variant="variant"
    :name="name"
    :size="size"
    :value="checkedValue"
    @change="$emit('change', localValue)"
    @input="$emit('input', localValue)"
  >
    <slot>{{ label }}</slot>
  </b-form-checkbox>
</template>

<script>
export default {
  name: 'FormCheckbox',
  props: {
    value: {
      type: [String, Number, Boolean, Array],
      default: false
    },
    checkedValue: {
      type: [String, Number, Boolean],
      default: true
    },
    name: {
      type: String,
      default: 'form-checkbox'
    },
    label: {
      type: String,
      default: ''
    },
    variant: {
      type: String,
      default: 'dark'
    },
    size: {
      type: String,
      default: 'md',
      validator (size) {
        return ['sm', 'md', 'lg', 'xxl'].includes(size)
      }
    }
  },
  data () {
    return {
      localValue: this.value
    }
  },
  watch: {
    value (propValue) {
      this.localValue = propValue
    }
  }
}
</script>
