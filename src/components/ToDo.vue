<template>
  <div class="todo-container" :id="id">
    <form ref="editForm" class="edit-form" @submit="(event) => {reRender(event, id)}">
      <input type="text" ref="editInput" class="edit-input deactivated" :value="msg" />
    </form>
    <p ref="msg" class="active">{{ msg }}</p>
    <div class="button-container">
      <button @click="remove(id)" type="button" class="delete-button">X</button>
      <button @click="edit()" type="button" class="edit-button">E</button>
    </div>
  </div>
</template>

<script>
export default {
  name: "ToDo",
  props: {
    msg: String,
    id: Number
  },
  methods: {
    remove(id) {
      this.$parent.$parent.remove(id);
    },
    edit() {
      const { msg, editInput, editForm } = this.$refs;
      msg.classList.remove('active');
      msg.classList.add('deactivated');
      editInput.classList.add('active');
      editInput.classList.remove('deactivated');
      editForm.style.display = 'block';
    },
    reRender(event, id) {
      event.preventDefault();
      const { msg, editInput, editForm } = this.$refs;
      this.$parent.$parent.edit(id, editInput.value);
      editInput.classList.remove('active');
      editInput.classList.add('deactivated');
      msg.classList.add('active');
      msg.classList.remove('deactivated');
      editForm.style.display = 'none';
    }
  }
};
</script>

<style scoped>
.todo-container {
  display: flex;
  justify-content: space-between;
  align-items: center;
  width: 100%;
}
.todo-container .edit-form {
  display: none;
}
button {
  background-color: transparent;
  border: none;
  padding: 5px;
  margin: 0 5px;
  cursor: pointer;
}
.delete-button {
  background-color: #ff7171;
}
.edit-button {
  background-color: #ffff6a;
}
.deactivated {
  display: none;
}
.active {
  display: block;
}
</style>
