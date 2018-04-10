<template>
  <div id="app">
    <img src="./assets/logo.png">
    <h1 class="ui huge header">Vue Todo</h1>
    <create-todo @create-todo="createTodo"></create-todo>
    <todo-list v-bind:todos="todos"></todo-list>
  </div>
</template>

<script>
//import TodoList component into the main vue file
import sweetalert from "sweetalert";
import TodoList from "./components/TodoList";
import CreateTodo from "./components/CreateTodo";

export default {
  name: "App",
  components: {
    // Add a reference to the TodoList component in the components property
    TodoList,
    CreateTodo
  },

  data() {
    return {
      todos: [
        {
          id: 1,
          title: "Create a Vue.js Todo List",
          project: "Learning Vue.js",
          done: false
        },
      ]
    };
  },
  methods: {
    createTodo(newTodo) {
      this.todos.push(newTodo);
      sweetalert("Success!", "To-Do created!", "success");
    }
  }
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-bottom: 30px;
}
</style>
