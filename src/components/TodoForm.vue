<template>
    <div class="todo-form">
      <input v-model="newTodo" @keyup.enter="addTodo" placeholder="Add a new todo" class="input" />
      <button @click="addTodo" class="btn">Add</button>
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        newTodo: '',
      };
    },
    methods: {
      addTodo() {
        if (this.newTodo.trim() !== '') {
          this.$emit('addTodo', this.newTodo);
          this.newTodo = '';
        }
      },
    },
  };
  </script>
  
  <style scoped>
  .todo-form {
    margin-bottom: 20px;
  }
  
  .input {
    padding: 10px;
    margin-right: 10px;
    width: 60%;
    border: 1px solid #ccc;
    border-radius: 4px;
  }
  
  .btn {
    padding: 10px;
    background-color: rgb(51, 96, 193);
    color: white;
    border: none;
    border-radius: 4px;
    cursor: pointer;
  }
  </style>
  