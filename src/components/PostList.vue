<template>
  <div v-if="posts.length > 0">
    <h3>Список пользователей</h3>
    <ul class="post-list">
      <post-item
        v-for="post in posts"
        :post="post"
        :key="post.id"
        @remove="$emit('remove', post)"
      />
    </ul>
  </div>
  <h3 v-else style="color: red">Список постов пуст</h3>
</template>
<script>
import PostItem from '@/components/PostItem';
export default {
  components: { PostItem },
  props: {
    posts: {
      type: Array,
      required: true,
    },
  },
};
</script>

<style scoped>
.post + .post {
  margin-top: 32px;
}
</style>
