<template>
  <ValidationProvider
    v-slot="validationContext"
    :name="name"
    :rules="rules"
    :vid="vid"
    :custom-messages="validationMessages"
  >
    <b-form-group
      :class="[formGroupClass, 'custom-form-group']"
      :label="label"
      :label-class="labelClass"
      :label-size="labelSize"
    >
      <template #label>
        <slot name="label" />
      </template>
      <b-input-group>
        <slot name="prepend"></slot>
        <b-form-input
          v-model="localValue"
          :class="[
            'custom-form-control',
            bgVariant ? `bg-${bgVariant}` : '',
            textVariant ? `text-${textVariant}` : '',
            inputClass,
          ]"
          :border-variant="borderVariant"
          :no-border="noBorder"
          :size="size"
          :rounded="rounded"
          :disabled="disabled"
          :type="type"
          :placeholder="placeholder"
          :state="getValidationState(validationContext)"
          @input="$emit('input', localValue)"
          @focus="($event) => $emit('focus', $event)"
          @focusout="($event) => $emit('focusout', $event)"
          @mouseout="($event) => $emit('mouseout', $event)"
          @mouseleave="($event) => $emit('mouseleave', $event)"
          @keyup.enter="($event) => $emit('enter', localValue)"
        />
        <slot name="append"></slot>
        <b-form-invalid-feedback>
          {{ validationContext.errors[0] }}</b-form-invalid-feedback
        >
      </b-input-group>
    </b-form-group>
  </ValidationProvider>
</template>

<script>
import { ValidationProvider } from 'vee-validate'

export default {
  name: 'FormInput',
  components: { ValidationProvider },
  props: {
    borderVariant: {
      type: String,
      default: '',
    },
    bgVariant: {
      type: String,
      default: '',
    },
    textVariant: {
      type: String,
      default: 'light-900',
    },
    noBorder: {
      type: Boolean,
      default: false,
    },
    rounded: {
      type: Boolean,
      default: false,
    },
    disabled: {
      type: Boolean,
      default: false,
    },
    size: {
      type: String,
      default: 'md',
      validator(size) {
        return ['sm', 'md', 'lg'].includes(size)
      },
    },
    type: {
      type: String,
      default: 'text',
      validator(type) {
        return ['text', 'number', 'email', 'password', 'tel'].includes(type)
      },
    },
    name: {
      type: String,
      default: '',
    },
    value: {
      type: [String, Number],
      default: '',
    },
    label: {
      type: String,
      default: '',
    },
    labelClass: {
      type: [String, Array, Object],
      default: '',
    },
    labelSize: {
      type: String,
      default: 'md',
      validator(labelSize) {
        return ['sm', 'md', 'lg'].includes(labelSize)
      },
    },
    formGroupClass: {
      type: [String, Array, Object],
      default: '',
    },
    inputClass: {
      type: [String, Array, Object],
      default: '',
    },
    placeholder: {
      type: String,
      default: null,
    },
    rules: {
      type: Object,
      default: () => {},
    },
    validationMessages: {
      type: Object,
      default: () => {},
    },
    iconAppend: {
      type: String,
      default: '',
    },
    iconAppendVariant: {
      type: String,
      default: '',
    },
    iconAppendDisabled: {
      type: String,
      default: '',
    },
    iconAppendStateDisabled: {
      type: Boolean,
      default: false,
    },
    iconAppendButton: {
      type: Boolean,
      default: false,
    },
    iconPrepend: {
      type: String,
      default: '',
    },
    iconPrependVariant: {
      type: String,
      default: '',
    },
    iconPrependDisabled: {
      type: String,
      default: '',
    },
    iconPrependStateDisabled: {
      type: Boolean,
      default: false,
    },
    iconPrependButton: {
      type: Boolean,
      default: false,
    },
    vid: {
      type: String,
      default: '',
    }
  },
  data() {
    return {
      localValue: this.value,
    }
  },
  watch: {
    value(propValue) {
      this.localValue = propValue
    },
  },
  methods: {
    getValidationState(validationContext) {
      const { dirty, validated, valid = null } = validationContext
      // Returns the contextual state (validation style) of the element being validated (false for invalid, true for valid, or null for no validation state)
      return dirty || validated ? valid : null
    },
  },
}
</script>
