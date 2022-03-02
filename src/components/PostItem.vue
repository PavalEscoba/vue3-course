<template>
  <li class="post">
    <div class="post-desk">
      <p><b>Название:</b> {{ post.title }}</p>
      <p><b>Описание:</b> {{ post.body }}</p>
    </div>
    <div class="post-btns">
      <my-button @click="$emit('remove', post)">Delete</my-button>
    </div>
  </li>
</template>

<script>
export default {
  name: 'PostItem',
  props: {
    post: {
      type: Object,
      required: true,
    },
  },
};
</script>

<style scoped>
.post {
  padding: 16px;
  border: 2px solid teal;
  border-radius: 8px;
  box-shadow: 3px 2px 5px 1px rgba(147, 144, 144, 0.3);
  display: flex;
  align-items: center;
  justify-content: space-between;
}

.post-desk p + p {
  margin-top: 16px;
}
</style>
