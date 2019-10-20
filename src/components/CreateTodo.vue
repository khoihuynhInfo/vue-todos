<template>
  <div id="myDIV" class="header">
    <h2 style="margin:5px">My To Do List</h2>
    <input 
      v-model="newTodoText"
      type="text" 
      id="myInput" 
      placeholder="Title...">
    <span class="addBtn" v-on:click="addTodo()">Add</span>
  </div>
</template>

<script>
export default {
  name: "create-todo",
  data: function() {
    return {
      newTodoText: ""
    }
  },
  methods: {
    addTodo: function() {
      if(!this.newTodoText.length) {
        alert("Value is not empty !")
      } else {
        this.$emit('create-todo-emit', this.newTodoText);
        this.newTodoText = '';
      }
    }
  },
}
</script>

<style scoped>
.header {
  background-color: #f44336;
  padding: 30px 40px;
  color: white;
  text-align: center;
}

.header:after {
  content: "";
  display: table;
  clear: both;
}

input {
  margin: 0;
  border: none;
  border-radius: 0;
  width: 71%;
  padding: 10px;
  float: left;
  font-size: 16px;
}

.addBtn {
  padding: 10px;
  width: 25%;
  background: #d9d9d9;
  color: #555;
  float: left;
  text-align: center;
  font-size: 16px;
  cursor: pointer;
  transition: 0.3s;
  border-radius: 0;
}

</style>

