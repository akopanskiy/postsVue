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
      <my-button @click="createPost" >
          Створити
      </my-button>
      <!-- <my-button @click="closeModal">Close</my-button> -->
    </form>
</template>

<script>
import shortid from "shortid";
import MyButton from './UI/MyButton.vue';

export default {
  components: { MyButton },
    
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
   closeModal() {
        this.$emit('update:show', false)
    }
  }
}
</script>

<style scoped>
form {
display: flex;
flex-direction: column;
}
input {
  width: 100%;
  padding: 10px 15px;
  margin-top: 15px;
  border: 1px solid tomato;
}

</style>