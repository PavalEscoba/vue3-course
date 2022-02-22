<template>
  <input class="input" :value="modelValue" @input="updateInput" />
</template>
<script>
export default {
  name: 'my-input',
  props: {
    modelValue: [String, Number],
  },
  methods: {
    updateInput(event) {
      this.$emit('update:modelValue', event.target.value);
    },
  },
};
</script>

<style scoped>
.input {
  width: 100%;
  max-width: 565px;
  margin-top: 16px;
  border: 2px solid teal;
  border-radius: 8px;
  padding: 8px;
}
</style>
