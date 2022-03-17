<template>
    <div class="post"  v-bind:key="post.id">
        <div>
    <div ><strong>Назва: </strong>{{post.title}}</div>
    <div><strong>Зміст: </strong>{{post.body}}</div>
    </div>
    <div >
        <my-button  @click="$emit('remove', post)">Видалити</my-button>
    </div>
    </div>
</template>

<script>

export default {
   
    props: {
        post: {
            type: Object,
            required: true
        }
    }
}
</script>

<style scoped>
.post {
    display: flex;
    justify-content: space-between;
  width: 50%;
  padding: 15px;
  border: 2px solid green;
  margin-top: 10px;
}
/* .btn_dlt {
  width: 70px;
  margin-top: 10px;
  padding: 5px;
  background: none;
  color: blue;
  border: 1px solid teal;
} */
</style>