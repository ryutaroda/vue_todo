<template>
  <div class="app">
    <form v-on:submit.prevent class="form">
      <input
        type="text"
        v-model="todo"
        class="todo-input"
        placeholder="ここに書く"
        @keypress.enter="addTodo"
      />
    </form>
    <ul class="list">
      <li
        class="todo"
        v-for="(todo,index) in filteredTodos"
        :key="todo.id"
        :class="{ editing: todo == editedTodo }"
      >
        <span class="viewMode" @dblclick="editTodo(todo)">{{ todo.text }}</span>
        <input
          class="editMode"
          @keypress.enter="doneEdit(todo)"
          @blur="doneEdit(todo)"
          v-model="todo.text"
        />

        <div class="delete" @click="removeTodo(index)">×</div>
      </li>
    </ul>
  </div>
</template>

<script>
// import Star from "../components/icons/Star";

var STORAGE_KEY = "todos";
var todoStorage = {
  fetch: function() {
    const todos = JSON.parse(localStorage.getItem(STORAGE_KEY) || "[]");
    todos.forEach((todo, index) => (todo.id = index));
    todoStorage.uid = todos.length;
    return todos;
  },
  save(todos) {
    localStorage.setItem(STORAGE_KEY, JSON.stringify(todos));
  }
};

export default {
  name: "TodoComponent",

  data() {
    return {
      todos: todoStorage.fetch(),
      todo: "",
      editedTodo: null
    };
  },
  watch: {
    todos: {
      handler(todos) {
        todoStorage.save(todos);
      },
      deep: true
    }
  },
  computed: {
    filteredTodos: function() {
      return this.todos;
    }
  },
  methods: {
    addTodo() {
      // 未入力の時追加しない
      if (this.todo === "") return;
      // 入植されたタスクを追加
      this.todos.push({
        id: todoStorage.uid++,
        // id: this.todos.length,
        text: this.todo
      });
      // 追加したら入力を空にする
      this.todo = "";
    },
    removeTodo(index) {
      // var index = this.todos.indexOf(todo)
      this.todos.splice(index, 1);
    },
    editTodo(todo) {
      this.editedTodo = todo;
    },
    doneEdit(todo) {
      if (!this.editedTodo) {
        return;
      }
      this.editedTodo = null;
      const text = todo.text.trim();
      if (text) {
        todo.text = text;
      } else {
        this.remove(todo);
      }
    }
  }
};
</script>

<style>
</style>
