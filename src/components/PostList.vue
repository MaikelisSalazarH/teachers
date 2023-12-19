<template>
    <div class="container">
        <PostDetail />
        <PostDetail />
        <PostDetail />
        <PostDetail />
        <PostDetail />
    </div>

</template>

<script lang="ts" setup>
    import PostDetail from './PostDetail.vue'; 

</script>
    
<style scoped>
  .container {
    display: flex;
    flex-wrap: wrap;
    flex-direction: row;
    justify-content: space-around;
  }
</style>
  