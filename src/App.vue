<template>
  <div id="app" class="container">
    <h1 style="text-align: center; margin: 2rem;">Stuff I Want To DO 🤡</h1>
    <form action="#" @submit.prevent="addTodo">
      <input type="text" v-model="newTodo" placeholder="Enter new todo 🤡" class="form-control" />

      <button class="btn btn-primary mt-3">Add Todo</button>
    </form>
    <ul id="example-1" class="list-group mt-3">
      <li
        class="list-group-item"
        v-for="todo in todos"
        v-bind:key="todo.id"
        v-on:click="toggleTodo(todo)"
        v-bind:class="{ completed: todo.done }"
      >
        <div class="list-item">
          {{ todo.title }}
          <button class="li-delete-button" v-on:click="deleteTodo(todo)">X</button>
        </div>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: "app",
  data() {
    return {
      newTodo: "",
      todos: []
    };
  },
  methods: {
    addTodo() {
      const todo = { title: this.newTodo, done: false, id: this.title };
      this.todos.push(todo);
      this.newTodo = "";
    },
    toggleTodo(todo) {
      todo.done = !todo.done;
      localStorage.setItem("todos", JSON.stringify(this.todos));
    },
    deleteTodo(todo) {
      const todoIndex = this.todos.indexOf(todo);
      this.todos.splice(todoIndex, 1);
    }
  },
  watch: {
    todos() {
      localStorage.setItem("todos", JSON.stringify(this.todos));
    },
    deep: true
  },
  mounted() {
    if (localStorage.getItem("todos")) {
      this.todos = JSON.parse(localStorage.getItem("todos"));
    }
  }
};
</script>

<style>
.completed {
  text-decoration: line-through;
  background-color: #f2efed;
}
.list-item {
  display: flex;
  justify-content: space-between;
}
.li-delete-button {
  border: none;
  border-radius: 3px;
  background-color: rgb(255, 86, 86);
  color: white;
}
</style>
