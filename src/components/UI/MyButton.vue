<template>
  <button class="btn">
    <slot></slot>
  </button>
</template>

<script>
export default {
  name: 'my-button',
};
</script>

<style scoped>
.btn {
  font-weight: 600;
  border: 2px solid teal;
  color: teal;
  padding: 8px;
  background-color: transparent;
}

.btn:hover {
  color: #aaa;
  border-color: #aaa;
  cursor: pointer;
}
</style>
