<template>
  <div id="app">
    <img src="./assets/logo.png">
    <h1 class="ui huge header">Vue Todo</h1>
    <todo-list v-bind:todos="todos"></todo-list>
  </div>
</template>

<script>
//import TodoList component into the main vue file
import TodoList from './components/TodoList';
import CreateTodo from "./components/CreateTodo";

export default {
  name: 'App',
  components: {
    // Add a reference to the TodoList component in the components property
    TodoList,
    CreateTodo,
  },

  data() {
    return {
      todos: [{
        id: 1,
        title: 'Todo A',
        project: 'Project A',
        done: false,
      }, {
        id: 2,
        title: 'Todo B',
        project: 'Project B',
        done: true,
      }, {
        id: 3,
        title: 'Todo C',
        project: 'Project C',
        done: false,
      }, {
        id: 4,
        title: 'Todo D',
        project: 'Project D',
        done: false,
      }],
    };
  },
  methods: {
    addTodo(title) {
      this.todos.push({
        id: Math.max(...this.todos.id) + 1,
        title,
        done: false,
      })
    }
  },
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
