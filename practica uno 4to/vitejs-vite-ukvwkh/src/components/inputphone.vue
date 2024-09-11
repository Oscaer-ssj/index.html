<template>
   <input type="number" name="phone" placeholder="phone">
</template>

<script>
import { defineComponent } from 'vue'

export default defineComponent({
  name: 'inputphone',
  props: {
    modelValue: String
  },
  emits: ['update:modelValue'],
  methods: {
    onInput(event) {
      this.$emit('update:modelValue', event.target.value)
    }
  }
})
</script>