<template>
  <div>
    <!-- JavaScript expressions in Vue are enclosed in double curly brackets. -->
    <p>Completed Tasks: {{todos.filter(todo => todo.done === true).length}}</p>
    <p>Pending Tasks: {{todos.filter(todo => todo.done === false).length}}</p>
    <todo @delete-todo="deleteTodo" v-for="todo in todos" :key="todo.id" :todo="todo"></todo>
  </div>
</template>

<script type = "text/javascript" >
import Todo from './Todo';

export default {
  props: ["todos"],
  components: {
    Todo,
  },
  methods: {
    deleteTodo(todo) {
      const todoIndex = this.todos.indexOf(todo);
      this.todos.splice(todoIndex, 1);
    },
  },
};
</script>

<style>

</style>