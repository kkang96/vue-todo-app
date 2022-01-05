<template>
  <section>
    <transition-group name="list" tag="ul">
      <li
        v-for="(todoItem, index) in this.$store.state.todoItems"
        class="shadow"
        v-bind:key="todoItem.item"
      >
        <i
          class="checkBtn fas fa-check"
          v-bind:class="{ checkBtnCompleted: todoItem.completed }"
          v-on:click="toggleComplete(todoItem, index)"
        ></i>
        <span v-bind:class="{ textCompleted: todoItem.completed }">
          {{ todoItem.item }}
        </span>
        <span class="removeBtn" v-on:click="removeTodo(todoItem, index)">
          <i class="removeBtn fas fa-trash-alt"></i>
        </span>
      </li>
    </transition-group>
  </section>
</template>

<script>
  export default {
    methods: {
      removeTodo(todoItem, index) {
        this.$store.commit('removeOneItem', { todoItem, index });
      },
      toggleComplete(todoItem, index) {
        this.$store.commit('toggleOneItem', { todoItem, index });
      },
    },
  };
</script>

<style scroped>
  ul {
    list-style: none;
    margin-top: 0;
    padding-left: 0px;
    text-align: left;
  }
  li {
    display: flex;
    height: 50px;
    min-height: 50px;
    margin: 0.5rem 0;
    padding: 0 0.9rem;
    background: #ffffff;
    border-radius: 5px;
    line-height: 50px;
  }
  .removeBtn {
    margin-left: auto;
    color: #ff6b66;
  }
  .checkBtn {
    margin-right: 5px;
    color: #facc61;
    line-height: 45px;
  }
  .checkBtnCompleted {
    color: #b3adad;
  }
  .textCompleted {
    color: #b3adad;
    text-decoration: line-through;
  }
  /* 리스트 아이템 트랜지션 효과 */
  .list-enter-active,
  .list-leave-active {
    transition: all 1s;
  }
  .list-enter, .list-leave-to /* .list-leave-active below version 2.1.8 */ {
    opacity: 0;
    transform: translateY(30px);
  }
</style>
