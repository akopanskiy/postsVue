<template>
  <button class="btn">
<slot></slot>
  </button>
</template>

<script>
export default {
name: 'my-button'
}
</script>

<style scoped>
.btn {
  width: 70px;
  margin-top: 10px;
  padding: 5px;
  background: none;
  color: blue;
  border: 1px solid teal;
}
</style>