<template>
  <form class="form" @submit.prevent>
    <h4>Create post</h4>
    <my-input v-model="post.name" type="text" placeholder="Name of post"></my-input>
    <my-input v-model="post.text" type="text" placeholder="Text here..." ></my-input>
    <my-btn @click="createPost" class="btn" >Add post</my-btn>
  </form>
</template>

<script>

export default {

  data() {
    return {
      post: {
        name: '',
        text: ''
      }
    }
  },
  methods: {
    createPost() {
      this.post.id = new window.Date();
      this.$emit('create', this.post);
      this.post = {
        name: '',
        text: ''
      }
    }
  }
}
</script>

<style >
</style>