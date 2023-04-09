<template>
    <div class="post">
       <div>
        <div><strong>{{ post.title }}</strong>
            <p>{{ post.body }}</p>
        </div>
       </div>

        <my-btn @click="$emit('remove',post)">Delete</my-btn>
    </div>
 
</template>

<script>

export default {
 
    props: {
        post: {
            type: Object,
            required: true,
        }
    },
}
</script>

<style scoped>
.post {
    margin: 10px 0;
    padding: 10px 0;
    border: 2px solid teal;
    display: flex;
    align-items: center;
    justify-content: space-between;
}
</style>