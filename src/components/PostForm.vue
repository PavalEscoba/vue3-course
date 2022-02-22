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
      v-model="post.body"
      class="input"
      type="text"
      placeholder="Description of a post"
    />
    <button @click="customCreate" class="btn">Create</button>
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
      this.post.id = Date.now();
      this.$emit('customCreate', this.post);
      this.post = {
        title: '',
        body: ''
      }
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
