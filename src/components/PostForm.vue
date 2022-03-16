<template>
    <form @submit.prevent>
      <h4>Написання поста</h4>
      <input 
      v-model="post.title"
     
       type="text" 
       placeholder="Назва">
       
      <input 
       v-model="post.body"
       type="text" 
       placeholder="Зміст">
       <!-- v-bind:value="post.body" 
      @input="post.body = $event.target.value" -->
      <button @click="createPost" class="btn">Створити</button>
    </form>
</template>

<script>
import shortid from "shortid"
export default {
    data () {
        return {
            post: {
                title: '',
                body: ''
            }
        }
    },
    methods: {
    createPost () {
      this.post.id = shortid.generate()
      this.$emit('create', this.post)
      this.post = {
          title: '',
          body: ''
      }
    },
   
  }
}
</script>

<style scoped>
form {
display: flex;
flex-direction: column;
}
input {
  width: 50%;
  padding: 10px 15px;
  margin-top: 15px;
  border: 1px solid tomato;
}
.btn {
  width: 70px;
  margin-top: 10px;
  padding: 5px;
  background: none;
  color: blue;
  border: 1px solid teal;
}
</style>