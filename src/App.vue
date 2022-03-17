
<template>
  <div class="base">
    <my-button @click="showModal">Створити пост</my-button>
    <my-modal v-model:show="modalVisible">
    <post-form @create="createPost"/>
    </my-modal>
    <post-list v-bind:posts="posts" @remove="removePost"/>
    
  </div>
</template>

<script>

import PostList from "./components/PostList.vue";
import PostForm from "./components/PostForm.vue";
 

export default {
  components: {
    PostList, PostForm
  },
  data () {
    return {
      posts: [
        {id: 1, title: 'JS', body: 'JS is the best)'},
        {id: 2, title: 'React', body: 'React is a framework of JS'},
        {id: 3, title: 'Vue', body: 'Vue is a framework of JS'},
      ],
      modalVisible: false
    }
  },
  methods: {
    createPost (post) {
      this.posts.push(post)
      this.modalVisible = false
    },
    removePost(post) {
      this.posts = this.posts.filter(p => p.id !== post.id)
    },
    showModal() {
      this.modalVisible = true
    }
  }
}
</script>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
.base {
  padding: 15px;
}


</style>
