<template>
  <div id="app">
    <div class="to-do-list">
      <h1 class="title">Vue To Do List</h1>
      <Input />
      <List />
    </div>
  </div>
</template>

<script>
import Input from "./components/Input.vue";
import List from "./components/List.vue";

export default {
  name: "app",
  components: {
    Input,
    List
  },
  data() {
    return {
      todos: [],
      add(todo) {
        this.todos.push(todo);
      },
      getTodoIById(id) {
        let index = 0;
        this.todos.forEach((todo, i) => {
          if (todo.id === id) index = i;
        });
        return index;
      },
      remove(id) {
        this.todos.splice(this.getTodoIById(id), 1);
      },
      edit(id, newMessage) {
        this.todos.splice(this.getTodoIById(id), 1, {
          msg: newMessage,
          id,
        });
      },
    };
  }
};
</script>

<style>
.to-do-list {
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
  position: absolute;
  top: 200px;
  left: 50%;
  transform: translateX(-50%);
  background-color: #e4e4e4;
  padding: 20px;
  border-radius: 10px;
}
.title {
  font-size: 1rem;
}
</style>
