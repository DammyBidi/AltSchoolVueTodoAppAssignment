<template>
  <div class="todo-app">
    <div class="todo-header">
      <h2>Todo App</h2>
    </div>
    <div class="todo-container">
      <TodoForm @addTodo="addTodo" />
      <div v-if="todos.length === 0" class="no-todos">No todos yet.</div>
      <TodoItem
        v-for="(todo, index) in todos"
        :key="index"
        :todo="todo"
        @deleteTodo="deleteTodo(index)"
        @editTodo="editTodo(index)"
        @saveTodo="saveTodo(index)"
      />
    </div>
  </div>
</template>

<script>
import TodoForm from './components/TodoForm.vue';
import TodoItem from './components/TodoItem.vue';

export default {
  components: {
    TodoForm,
    TodoItem,
  },
  data() {
    return {
      todos: [],
    };
  },
  methods: {
    addTodo(newTodo) {
      this.todos.push({ text: newTodo, editing: false });
    },
    deleteTodo(index) {
      this.todos.splice(index, 1);
    },
    editTodo(index) {
      this.todos[index].editing = true;
    },
    saveTodo(index) {
      this.todos[index].editing = false;
    },
  },
};
</script>

<style>
body {
  font-family: 'Arial', sans-serif;
  margin: 0;
  padding: 0;
  background-color: #f8f8f8;
}

.todo-app {
  max-width: 600px;
  margin: 50px auto;
  background-color: #fff;
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
  border-radius: 8px;
  overflow: hidden;
}

.todo-header {
  background-color: rgb(51, 96, 193);
  color: #fff;
  padding: 20px;
  text-align: center;
}

.todo-container {
  padding: 20px;
}

.no-todos {
  text-align: center;
  color: #888;
  margin-top: 20px;
}

</style>
