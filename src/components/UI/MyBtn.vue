<template>
    <button class="btn">
        <slot></slot>
   </button>
</template>

<script>
export default {
    name:"my-btn",
}
</script>

<style>
.btn {
    left: 0;
    padding: 7px;
    background: none;
    color: teal;
    border: 1px solid teal;
    border-radius: 5px;
}
</style>