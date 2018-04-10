<template>
  <div>
    <!-- JavaScript expressions in Vue are enclosed in double curly brackets. -->
    <p>Completed Tasks: {{todos.filter(todo => todo.done === true).length}}</p>
    <p>Pending Tasks: {{todos.filter(todo => todo.done === false).length}}</p>
    <todo
      @delete-todo="deleteTodo"
      @complete-todo="completeTodo"
      v-for="todo in todos" :key="todo.id" :todo.sync="todo">
    </todo>
  </div>
</template>

<script type = "text/javascript" >
import Todo from './Todo';
import sweetalert from 'sweetalert';

export default {
  props: ["todos"],
  components: {
    Todo,
  },
  methods: {
    deleteTodo(todo) {
        const todoIndex = this.todos.indexOf(todo);
        this.todos.splice(todoIndex, 1);
        sweetalert('Deleted!', 'Your To-Do has been deleted.', 'success');
    },
    completeTodo(todo) {
      const todoIndex = this.todos.indexOf(todo);
      if (!this.todos[todoIndex].done) {
        this.todos[todoIndex].done = true;
        sweetalert('Success!', 'To-Do completed!', 'success');
      } else {
        this.todos[todoIndex].done = false;
        sweetalert("It's back on the list!", 'Get yo shit done!', 'warning')
      }
    },
  },
};
</script>

<style>

</style>