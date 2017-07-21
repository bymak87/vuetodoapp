<template>
  <div>
    <p>Completed Tasks: {{todos.filter(todo => {return todo.done === true}).length}}</p>
    <p>Pending Tasks: {{todos.filter(todo => {return todo.done === false}).length}}</p>
    <todo v-on:delete-todo="deleteTodo" v-on:complete-todo="completeTodo" v-for="todo in todos" v-bind:todo="todo" :key="todo.id"></todo>
  </div>
</template>

<script>
import Todo from './Todo';
export default {
  props: ['todos'],
  components: {
    Todo
  },
  methods:{
    completeTodo(todo) {
      const todoIndex = this.todos.indexOf(todo);
      this.todos[todoIndex].done = ture;
    },
    deleteTodo(todo){
      const todoIndex = this.todos.indexOf(todo);
      this.todos.splice(todoIndex, 1);
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
