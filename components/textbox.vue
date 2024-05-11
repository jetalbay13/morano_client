<template>
    <div class="textbox">
      <label :for="id" class="text-sm font-medium mb-1 block">
        {{ label }}
      </label>
      <input
        :id="id"
        :type="type"
        :placeholder="placeholder"
        v-bind:value="value"
        @input="$emit('update:value', $event.target.value)"
        class="border rounded-md px-3 py-2 w-full focus:outline-none focus:ring-blue-500 focus:ring-1"
      />
    </div>
  </template>
  
  <script>
  export default {
  props: {
    label: String,
    id: String,
    type: {
      type: String,
      default: 'text',
    },
    placeholder: String,
    value: {
      type: [String, Number],
      default: '',
    },
  },
  watch: {
    value(newVal) {
      // Optional: Handle changes to the value prop here (if needed)
      this.$emit('update:value', newVal)
    }
  },
};
  </script>
  
  <style scoped>
  /* Add custom styles for the textbox here */
  </style>