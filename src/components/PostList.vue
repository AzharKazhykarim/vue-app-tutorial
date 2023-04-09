
<template>
  <post-item
      v-if="posts.length>0"
      v-for="post in posts" :post="post"
      key="post.id"
      @remove="$emit('remove',post)"></post-item>
  <h1 v-else>There is no posts!</h1>
</template>

<script>

import PostItem from "@/components/PostItem"

export default {
  components: {
    PostItem
  },
  props: {
    posts: {
      type: Array,
      required: true,
    }
  }
}

</script>

<style scoped>

</style>