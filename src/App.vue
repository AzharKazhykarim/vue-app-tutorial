<template>
  <div class="app">
    <h1>Post page</h1>
<div class="app_btns">
  <my-btn @click="showDialog">Create post</my-btn>
  <my-select v-model="selectedSort"></my-select>
</div>
    <my-dialog v-model:show="dialogVisible">
      <post-form @create="createPost"></post-form>
    </my-dialog>
    <post-list :posts="posts" @remove="deletePost" v-if="!isPostLoading"></post-list>
    <div v-else>Loading...</div>
  </div>
</template>

<script>
import PostForm from "@/components/PostForm";
import PostList from "@/components/PostList";
import MyDialog from "@/components/UI/MyDialog";
import axios from "axios";
import MyBtn from "@/components/UI/MyBtn";
import MySelect from "@/components/UI/MySelect";

export default {
  components: {
    MySelect,
    MyBtn,
    MyDialog,
    PostForm,
    PostList,
  },
  data() {
    return {
      posts: [],
      dialogVisible: false,
      isPostLoading: false,
      selectedSort:''
    };
  },
  methods: {
    createPost(post) {
      this.posts.push(post);
      this.dialogVisible = false;
    },
    deletePost(post) {
      this.posts = this.posts.filter(pt => pt.id !== post.id)
    },
    showDialog() {
      this.dialogVisible = true;
    },
    async fetchPosts() {
      try {
        this.isPostLoading = true;
        const response = await axios.get("https://jsonplaceholder.typicode.com/posts?_limit=10");
        this.posts = response.data;
      } catch (e) {
        alert("Error!")
      }
      finally {
        this.isPostLoading = false;
      }
    },
  },
  mounted() {
    this.fetchPosts();
  },
};
</script>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

.app {
  padding: 20px;
}
.app_btns{
  display: flex;
  justify-content: space-between;
  margin: 15px 0;
}
</style>
