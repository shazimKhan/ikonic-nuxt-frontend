<template>
  <b-form-checkbox
    v-model="checked"
    :squared="squared"
    :variant="variant"
    :name="name"
    :size="size"
    :inline="inline"
    switch
    @change="$emit('change', checked)"
    @input="$emit('input', checked)"
  >
    <template #default>
      <slot name="default" />
    </template>
  </b-form-checkbox>
</template>

<script>
export default {
  name: 'FormSwitch',
  props: {
    squared: {
      type: Boolean,
      default: false,
    },
    variant: {
      type: String,
      default: '',
    },
    name: {
      type: String,
      default: 'form-switch',
    },
    size: {
      type: String,
      default: 'md',
      validator(size) {
        return ['sm', 'md', 'lg', 'xl', 'xxl'].includes(size)
      },
    },
    inline: {
      type: Boolean,
      default: false,
    },
    value: {
      type: [Boolean, Number, String],
      default: true,
    },
  },
  data() {
    return {
      checked: this.value,
    }
  },
  watch: {
    value(newVal) {
      this.checked = newVal
    },
  },
}
</script>
