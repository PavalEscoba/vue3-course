<template>
  <div class="app">
    <h1>Page with posts</h1>
    <my-button @click="showDialog"> Create Post </my-button>
    <MyDialog v-model:show="dialogVisible">
      <post-form @customCreate="createPost" />
    </MyDialog>
    <p v-if="isLoading">Loading...</p>
    <post-list v-else :posts="posts" @remove="removePost" />
  </div>
</template>
<script>
import axios from 'axios';
import PostForm from '@/components/PostForm';
import PostList from '@/components/PostList';
import MyDialog from '@/components/UI/MyDialog.vue';
import MyButton from './components/UI/MyButton.vue';

export default {
  components: {
    PostForm,
    PostList,
    MyDialog,
    MyButton,
  },
  data() {
    return {
      posts: [],
      dialogVisible: false,
      isLoading: false,
    };
  },
  methods: {
    createPost(post) {
      this.posts.push(post);
      this.dialogVisible = false;
    },
    removePost(post) {
      this.posts = this.posts.filter((postItem) => postItem.id !== post.id);
    },
    showDialog() {
      this.dialogVisible = true;
      console.log('showed');
    },
    async fetchPosts() {
      try {
        const response = await axios.get(
          'https://jsonplaceholder.typicode.com/posts?_limit=10'
        );
        this.posts = response.data;
        this.isLoading = false;
      } catch (error) {
        alert(error.message);
      }
    },
  },
  beforeCreate() {},
  mounted() {
    this.isLoading = true;
    this.fetchPosts();
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
