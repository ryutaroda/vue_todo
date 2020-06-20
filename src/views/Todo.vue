<template>
  <div id="todo">
    <TodoHeader />
    <TodoComponent />
    <!-- <TodoCreater @add-todo="addTodo" /> -->
    <!-- <TodoList :todos="todos" :filtered-todos="filteredTodos" @remove-todo="removeTodo" /> -->
  </div>
</template>

<script>
import TodoHeader from "../components/TodoHeader.vue";
import TodoComponent from "../components/TodoComponent.vue";
// import TodoCreater from "../components/TodoCreater.vue";

// var STORAGE_KEY = "todos";
// var todoStorage = {
//   fetch: function() {
//     const todos = JSON.parse(localStorage.getItem(STORAGE_KEY) || "[]");
//     todos.forEach((todo, index) => (todo.id = index));
//     todoStorage.uid = todos.length;
//     return todos;
//   },
//   save(todos) {
//     localStorage.setItem(STORAGE_KEY, JSON.stringify(todos));
//   }
// };

export default {
  name: "Todo",
  components: {
    TodoHeader,
    TodoComponent
    // TodoCreater
  }
  // data() {
  //   return {
  //     todos: todoStorage.fetch()
  //   };
  // },
  // watch: {
  //   todos: {
  //     handler(todos) {
  //       todoStorage.save(todos);
  //     },
  //     deep: true
  //   }
  // },
  // computed: {
  //   filteredTodos: function() {
  //     return this.todos;
  //   }
  // },
  // methods: {
  //   addTodo() {
  //     // 未入力の時追加しない
  //     if (this.newTodo === "") return;
  //     // 入植されたタスクを追加
  //     this.todos.push({
  //       id: todoStorage.uid++,
  //       // id: this.todos.length,
  //       text: this.newTodo
  //     });
  //     // 追加したら入力を空にする
  //     this.newTodo = "";
  //   },
  //   removeTodo(index) {
  //     // var index = this.todos.indexOf(todo)
  //     this.todos.splice(index, 1);
  //   },
  //   editTodo(todo) {
  //     this.editedTodo = todo;
  //   },
  //   doneEdit(todo) {
  //     if (!this.editedTodo) {
  //       return;
  //     }
  //     this.editedTodo = null;
  //     const text = todo.text.trim();
  //     if (text) {
  //       todo.text = text;
  //     } else {
  //       this.remove(todo);
  //     }
  //   }
  // }
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
