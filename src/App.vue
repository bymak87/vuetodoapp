<template>
  <div id="app">
    <!-- <img src="./assets/logo.png"> -->
    <todo-list v-bind:todos="todos"></todo-list>
    <create-todo v-on:add-todo="addTodo"></create-todo>
  </div>
</template>

<script>
import TodoList from './components/TodoList';
import CreateTodo from './components/CreateTodo';

export default {
  name: 'app',
  components: {
    TodoList,
    CreateTodo,
  },
  methods: {
    addTodo(title){
      this.todos.push({
        title,
        done: false,
      });
    }
  },
  data() {
    return {
      todos:[{
        title: 'Todo A',
        project: 'Project A',
        done: false,
        id: 1,
      }, {
        title: 'Todo B',
        project: 'Project B',
        done: true,
        id: 2,
      }, {
        title: 'Todo C',
        project: 'Project C',
        done: false,
        id: 32,
      }, {
        title: 'Todo D',
        project: 'Project D',
        done: false,
        id: 23,
      }]
    }

  }
}
</script>

<style>

</style>
