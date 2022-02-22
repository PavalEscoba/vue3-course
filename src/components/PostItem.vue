<template>
  <div class="post">
    <p><b>Название:</b> {{ post.title }}</p>
    <p><b>Описание:</b> {{ post.body }}</p>
  </div>
  <div class="post-btns">
    <button class="post-btn--edit">
      Edit
    </button>
    <button class="post-btn--delete">
      Delete
    </button>
  </div>
</template>

<script>
export default {
  name: "PostItem",
  props: {
    post: {
      type: Object,
      required: true
    }
  }
}
</script>

<style scoped>
  .post {
    padding: 16px;
    border: 2px solid teal;
    border-radius: 8px;
    box-shadow: 3px 2px 5px 1px rgba(147, 144, 144, 0.3);
    display: flex;
    flex-direction: column;
  }
</style>