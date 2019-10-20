<template>
  <div id="app">
    <CreateTodo v-on:create-todo-emit="addTodo" />
    <TodoList v-bind:todos="listTodo" />
  </div>
</template>


<script>

import CreateTodo from './components/CreateTodo'
import TodoList from './components/TodoList'

export default {
  name: 'app',
  data: function() {
    return {
      listTodo: [
        { id: 1, text: "foo" },
        { id: 2, text: "bar" },
      ]
    }
  },
  methods: {
    createId: function() {
      return Math.random().toString(36).replace(/[^a-z]+/g, '').substr(0, 9);
    },
    addTodo: function(newValue) {
      const newId = this.createId();
      this.listTodo.push({ id: newId, text: newValue });
    }
  },
  components: {
    CreateTodo,
    TodoList,
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}

body {
  margin: 0;
  min-width: 250px;
}
</style>
