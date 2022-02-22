<template>
  <form @submit.prevent>
    <h3>Create a post</h3>
    <my-input v-model="post.title" type="text" placeholder="Name of a post" />
    <my-input
      v-model="post.body"
      type="text"
      placeholder="Description of a post"
    />
    <my-button
      @click="customCreate"
      class="btn"
      style="margin-top: 16px; align-self: flex-start"
      >Create</my-button
    >
  </form>
</template>
<script>
export default {
  data() {
    return {
      post: {
        title: '',
        body: '',
      },
    };
  },
  methods: {
    customCreate() {
      if (!this.post.title || !this.post.body) {
        alert('no text');
        return;
      }
      this.post.id = Date.now();
      this.$emit('customCreate', this.post);
      this.post = {
        title: '',
        body: '',
      };
    },
  },
};
</script>

<style scoped>
form {
  margin-bottom: 32px;
  display: flex;
  flex-direction: column;
}
</style>
