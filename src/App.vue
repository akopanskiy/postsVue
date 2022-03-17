
<template>
  <div class="base">
    <input type="text" v-model="searchPost">
    <div class="function_btns">
      <my-button @click="showModal">Створити пост</my-button>
      <my-select v-model="selectedSort" :options="sortOptions"/>
    </div>
    
    <my-modal v-model:show="modalVisible">
    <post-form @create="createPost" v-model:show="modalVisible"/>
    </my-modal>
    <post-list v-bind:posts="filterPosts" @remove="removePost"/>
    
  </div>
</template>

<script>

import PostList from "./components/PostList.vue";
import PostForm from "./components/PostForm.vue";
import axios from 'axios';

export default {
  components: {
    PostList, PostForm
  },
  data () {
    return {
      posts: [],
      modalVisible: false,
      searchPost: '',
      selectedSort: '',
      sortOptions: [
        {value: 'title', name: 'За назвою'},
        {value: 'body', name: 'За змістом'}
      ]
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
    },
    async fetchPosts () {
      try {
        const res = await axios.get('https://jsonplaceholder.typicode.com/posts?_limit=10')
        this.posts = res.data
      } catch (error) {
        alert('Ой')
      }
    }
  },
  mounted () {
    this.fetchPosts()
  },
  computed: {
    // selectedSort(newValue) {
    //   this.posts.sort( (a, b) => {
    //     return a[newValue]?.localeCompare(b[newValue])
    //   })
    // },
    sortedPosts() {
      return [...this.posts].sort((a, b) => a[this.selectedSort]?.localeCompare(b[this.selectedSort]))
    },
    filterPosts() {
      return this.sortedPosts.filter(p => p.title.includes(this.searchPost))
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
.function_btns {
  display: flex;
  justify-content: space-between;
  width: 50%;
}

</style>
