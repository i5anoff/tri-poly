<template>
  <div class="sidebar-control">
    <div class="control-header">
      <div class="control-label">
        <span>{{ label }}</span>
      </div>
    </div>
    <div class="control-header">
      <input :disabled="disabled" class="custom-range" type="range" :min="min" :max="max" :step="step" :value="value" @input="onInput">
      <div class="control-output">
        <input :disabled="disabled" type="text" :value="value" @change="onInput">
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Slider',
  props: {
    disabled: {
      type: Boolean,
      default: false
    },
    min: {
      type: Number,
      default: 0
    },
    max: {
      type: Number,
      default: 100
    },
    step: {
      type: Number,
      default: 1
    },
    label: {
      type: String,
      default: 'Label'
    },
    value: {
      type: Number,
      default: 50
    }
  },
  methods: {
    onInput ($event) {
      if ($event.target.value > this.min) {
        this.$emit('input', $event.target.value)
      } else {
        this.$emit('input', this.min)
      }
      if ($event.target.value < this.min) {
        this.$emit('input', this.min)
      }
    }
  }
}
</script>
