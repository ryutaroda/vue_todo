<template>
  <div class="app">
    <form v-on:submit.prevent class="form">
      <input
        type="text"
        v-model="newTodo"
        class="todo-input"
        placeholder="ここに書く"
        @keypress.enter="addTodo"
      />
    </form>
  </div>
</template>

<script>
export default {
  name: "TodoCreater",
  data() {
    return {
      newTodo: ""
    };
  },
  methods: {
    addTodo() {
      if (this.newTodo === "") return;
      console.log("addTodoした");
      this.$emit("add-todo", this.newTodo);
      this.newTodo = "";
    }
  }
};
</script>

<style>
</style>