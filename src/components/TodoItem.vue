<template>
  <div class="todo-item">
    <div v-if="!todo.editing" class="todo-text">
      <input type="checkbox" class="checkbox" />
      <span>{{ todo.text }}</span>
    </div>
    <div v-else class="edit-form">
      <input v-model="todo.text" @keyup.enter="saveTodo" class="input" />
      <button @click="saveTodo" class="btn-save"><img src="@/Icons/Save.svg" alt="Save Icon" class="icon" /></button>
    </div>
    <div class="icon-buttons">
      <button @click="editTodo" class="btn-edit"><img src="@/Icons/Edit.svg" alt="Edit Icon" class="icon" /></button>
      <button @click="deleteTodo" class="btn-delete"><img src="@/icons/Delete.svg" alt="Delete Icon" class="icon" /></button>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    todo: Object,
  },
  methods: {
    deleteTodo() {
      this.$emit('deleteTodo');
    },
    editTodo() {
      this.$emit('editTodo');
    },
    saveTodo() {
      this.$emit('saveTodo');
    },
  },
};
</script>

<style scoped>
.todo-item {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 15px;
  margin: 15px 0;
  background-color: #fff;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
  border-radius: 8px;
}

.todo-text {
  display: flex;
  align-items: center;
}

.checkbox {
  margin-right: 10px;
}

.input {
  padding: 8px;
  margin-right: 8px;
  width: 60%;
  border: 1px solid #ccc;
  border-radius: 4px;
}

.btn {
  padding: 8px;
  cursor: pointer;
  border: none;
  border-radius: 4px;
}

.icon-buttons {
  display: flex;
}

.btn-edit {
  background-color: white;
  color: white;
  margin-right: 5px;
}

.btn-save {
  background-color: white;
  color: white;
}

.btn-delete {
  background-color: rgb(51, 96, 193);
  color: white;
}
</style>
