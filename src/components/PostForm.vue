<template>
  <form @submit.prevent>
    <h3>Create a post</h3>
    <input
      v-model="post.title"
      class="input"
      type="text"
      placeholder="Name of a post"
    />
    <input
      v-bind:value="post.body"
      @input="post.body = $event.target.value"
      class="input"
      type="text"
      placeholder="Description of a post"
    />
    <button @click="createPost" class="btn">Create</button>
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
    createPost() {
      this.post.id = Date.now();
      console.log(this.post);
      this.$emit('create', this.post);
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

.input {
  width: 100%;
  max-width: 565px;
  margin-top: 16px;
  border: 2px solid teal;
  border-radius: 8px;
  padding: 8px;
}

.btn {
  margin-top: 16px;
  font-weight: 600;
  border: 2px solid teal;
  color: teal;
  padding: 8px;
  background-color: transparent;
  align-self: flex-start;
}

.btn:hover {
  color: #aaa;
  border-color: #aaa;
  cursor: pointer;
}
</style>
