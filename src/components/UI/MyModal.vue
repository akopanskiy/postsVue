<template>
  <div class="modal" v-if="show"
   >
   <!-- @click="closeModal" -->
      <div class="modal_content">
          <slot></slot>
          <!-- <my-button @click="closeModal">Close</my-button> -->
      </div>
  </div>
</template>

<script>
export default {
name: 'my-modal',
props: {
    show: {
        type: Boolean,
        default: false
    }
},
methods: {
    closeModal() {
        this.$emit('update:show', false)
    }
}
}
</script>

<style>
.modal {
    position: fixed;
    display: flex;
    top: 0;
    right: 0;
    bottom: 0;
    left: 0;
    background: rgba(0, 0, 0, 0.5);
}
.modal_content {
    margin: auto;
    background: #FFF;
    min-width: 500px;
    min-height: 100px;
    padding: 15px;
}
</style>