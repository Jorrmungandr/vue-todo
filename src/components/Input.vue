<template>
  <form @submit.prevent="onSubmit" class="input-container">
    <input ref="input" type="text" placeholder="add-todo" />
    <button type="submit">Send Todo</button>
  </form>
</template>

<script>
export default {
  name: "Input",
  methods: {
    onSubmit(event) {
      event.preventDefault();
      const { input } = this.$refs;
      if (input.value === '') return;
      this.$parent.add({
        msg: input.value,
        id: new Date().getTime(),
      });
      input.value = '';
    }
  }
};
</script>

<style scoped>
.input-container {
  display: flex;
}
</style>
