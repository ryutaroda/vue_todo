<template>
  <div>
    <input
      type="text"
      v-model="todo"
      class="todo-input"
      placeholder="ここに書く"
      @keypress.enter="addTask"
    />
    <input
      class="editMode"
      @keypress.enter="doneEdit(todo)"
      @blur="doneEdit(todo)"
      v-model="todo.text"
    />
    <div class="delete" @click="remove(index)">×</div>
  </div>
</template>

<script>
export default {
  name: "TodoItem",
  props: {
    todo: Object
  },
  data() {
    return {
      editedTodo: null
    };
  }
};
</script>

<style>
</style>