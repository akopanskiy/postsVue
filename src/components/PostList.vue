<template>
    <div v-if="posts.length > 0" >
        <h3>Список постів</h3>
    <post-item 
    v-for="post in posts"
     v-bind:key="post.id"
     :post="post"
     @remove="$emit('remove', post)"
     />
    </div>
    <h2 v-else>Ой лишенько! Хай йому грець! Все пропало!)</h2>
</template>

<script>
import PostItem from "./PostItem.vue";

export default {
    components: {PostItem},
    props: {
        posts: {
            type: Array,
            required: true
        }
    }
}
</script>

<style scoped>
.post {
  width: 50%;
  padding: 15px;
  border: 2px solid green;
  margin-top: 10px;
}
</style>