<template>
  <div class="form-control">
    <label :for="id">{{ label }}</label>
    <input
      :class="{ invalid: error }"
      type="text"
      :id="id"
      :placeholder="placeholder"
      :value="modelValue"
      @input="onChange"
    />
    <span v-if="error" class="error-name">{{ error }}</span>
  </div>
</template>

<script>
export default {
  emits: ['update:modelValue'],
  props: {
    label: String,
    error: String,
    placeholder: String,
    modelValue: String,
  },
  methods: {
    onChange(e) {
      this.$emit('update:modelValue', e.target.value);
    },
  },
  data() {
    return {
      id: `input-${Math.random()}`,
    };
  },
};
</script>
