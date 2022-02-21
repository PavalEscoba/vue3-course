<template>
  <h1>Posts</h1>
  <post-form @create="createPost" />
  <post-list :posts="posts" />
</template>
<script>
import PostForm from '@/components/PostForm';
import PostList from '@/components/PostList';

export default {
  components: {
    PostForm,
    PostList,
  },
  data() {
    return {
      posts: [
        { id: 1, title: 'Family', body: 'Love resposibility strength 1' },
        { id: 2, title: 'Work', body: 'Love resposibility strength 2' },
        { id: 1, title: 'Spirit', body: 'Love resposibility strength 3' },
      ],
    };
  },
  methods: {
    createPost(post) {
      this.posts.push(post);
      console.log(this.posts);
    },
  },
};
</script>

<style>
*,
*::before,
*::after {
  box-sizing: border-box;
  padding: 0;
  margin: 0;
  font-family: sans-serif;
}
h1 {
  margin-bottom: 36px;
}
body {
  width: 100%;
  max-width: 1140px;
  margin: 0 auto;
  padding: 0 16px;
}
</style>
