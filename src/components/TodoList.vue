<template>
  <ul>
    <li 
      is="todo-item"
      v-for="item in todos"
      v-bind:key="item.id"
      v-bind:item="item"
      v-on:remove-item-emit="removeItem">
    </li>
  </ul>
</template>

<script>
import TodoItem from './TodoItem';
export default {
  name: "todo-list",
  props: {
    todos: Array
  },
  methods: {
    removeItem: function(idItem) {
      const todoIndex = this.todos.findIndex(item => item.id === idItem);
      this.todos.splice(todoIndex, 1);
    }
  },
  components: {
    TodoItem,
  }
}
</script>

<style scoped>
  ul {
    margin: 0;
    padding: 0;
  }
</style>

