<template>
  <div class="clearAllContainer">
    <span class="clearAllBtn" v-on:click="clearTodo">Clear All</span>
  </div>
</template>

<script>
  export default {
    methods: {
      clearTodo() {
        this.$emit('clearAll');
      },
    },
  };
</script>

<style scoped>
  .clearAllContainer {
    width: 8.5rem;
    height: 50px;
    margin: 0 auto;
    background: #ffffff;
    border-radius: 5px;
    line-height: 50px;
  }
  .clearAllBtn {
    display: block;
    color: #ff6b66;
    font-weight: bolder;
  }
</style>
