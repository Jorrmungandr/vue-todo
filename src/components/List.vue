<template>
  <ul class="list">
    <li class="li-item" v-for="todo in todos" :key="todo.id">
      <ToDo :msg="todo.msg" :id="todo.id" />
    </li>
  </ul>
</template>

<script>
import ToDo from './ToDo';

export default {
  name: 'List',
  components: {
    ToDo,
  },
  data() {
    return {
      todos: this.$parent.todos,
    };
  },
};
</script>

<style scoped>
.list {
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
  width: 100%;
  padding: 0;
  max-height: 200px;
  overflow: auto;
}
.li-item {
  list-style: none;
  width: 100%;
}
</style>
