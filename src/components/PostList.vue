<template>
  <div class="post" v-for="post in posts" :key="post.id">
    <p><b>Название:</b> {{ post.title }}</p>
    <p><b>Описание:</b> {{ post.body }}</p>
  </div>
</template>
<script>
export default {
  props: {
    posts: {
      type: Array,
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
}
.post + .post {
  margin-top: 32px;
}
</style>
