<template>
  <div class="inputBox shadow">
    <input type="text" v-model="newTodoItem" v-on:keyup.enter="addTodo" />
    <span class="addContainer" v-on:click="addTodo">
      <i class="fas fa-plus addBtn"></i>
    </span>

    <Modal v-if="showModal" @close="showModal = false">
      <h3 slot="header">※ 경고 ※</h3>
      <div slot="body">ToDo 내용을 입력해주세요.</div>
      <div slot="footer">
        <span class="closeModalBtn" @click="showModal = false">확인</span>
      </div>
    </Modal>
  </div>
</template>

<script>
  import Modal from './common/Modal.vue';

  export default {
    data() {
      return {
        newTodoItem: '',
        showModal: false,
      };
    },
    methods: {
      addTodo() {
        if (this.newTodoItem !== '') {
          this.$emit('addTodoItem', this.newTodoItem);
          this.clearInput();
        } else {
          this.showModal = !this.showModal;
        }
      },
      clearInput() {
        this.newTodoItem = '';
      },
    },
    components: {
      Modal,
    },
  };
</script>

<style scoped>
  input:focus {
    outline: none;
  }
  .inputBox {
    height: 50px;
    background: #ffffff;
    border-radius: 5px;
    line-height: 50px;
  }
  .inputBox input {
    width: 75%;
    border-style: none;
    font-size: 0.9rem;
  }
  .addContainer {
    display: block;
    float: right;
    width: 3rem;
    background: linear-gradient(to right, #fff382, #ffbb1d);
    border-radius: 0 5px 5px 0;
  }
  .addBtn {
    color: #ffffff;
    vertical-align: middle;
  }
  .closeModalBtn {
    padding: 10px 50px;
    background: #ffbb1d;
    color: #ffffff;
    border-radius: 5px;
  }
</style>
