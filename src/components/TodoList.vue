<template>
  <div>
    <ul class="list">
      <li
        class="todo"
        v-for="todo in filteredTodos"
        :key="todo.id"
        :class="{ editing: todo == editedTodo }"
      >
        <TodoItem :todo="todo" @remove-todo="removeTodo" />
      </li>
    </ul>
  </div>
</template>

<script>
import TodoItem from "../components/TodoItem.vue";

export default {
  name: "TodoList",
  components: {
    TodoItem
  },
  props: {
    todos: Array,
    filteredTodos: Array
  },
  nethods: {
    removeTodo(todo) {
      this.$emit("remove-todo", todo);
    }
  }
};
</script>

<style>
.editing .editMode {
  display: block;
}
.editing .viewMode {
  display: none;
}
.editMode {
  display: none;
}
</style>