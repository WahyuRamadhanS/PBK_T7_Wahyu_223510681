<!-- src/components/TodoList.vue -->
<template>
  <div class="container">
    <h1>Todo List</h1>
    <div class="input-group">
      <input v-model="newTodo" @keyup.enter="addNewTodo" placeholder="Add a new todo" />
      <button @click="addNewTodo">Add</button>
    </div>
    <ul>
      <li v-for="(todo, index) in todos" :key="index">
        <div class="todo-text">
          <input type="checkbox" v-model="todo.completed" @change="toggleTodoStatus(index)" />
          <span :class="{ completed: todo.completed }">{{ todo.text }}</span>
        </div>
        <button class="delete-btn" @click="deleteTodo(index)">Delete</button>
      </li>
    </ul>
    <p>Incomplete tasks: {{ incompleteTodosCount }}</p>
  </div>
</template>

<script>
import { ref } from 'vue';
import { useTodoStore } from '../stores/todoStore';

export default {
  setup() {
    const todoStore = useTodoStore();
    const newTodo = ref('');

    const addNewTodo = () => {
      if (newTodo.value.trim() !== '') {
        todoStore.addTodo(newTodo.value);
        newTodo.value = '';
      }
    };

    const deleteTodo = (index) => {
      todoStore.removeTodo(index);
    };

    const toggleTodoStatus = (index) => {
      todoStore.toggleTodo(index);
    };

    return {
      newTodo,
      addNewTodo,
      deleteTodo,
      toggleTodoStatus,
      todos: todoStore.todos,
      incompleteTodosCount: todoStore.incompleteTodosCount,
    };
  },
};
</script>

<style scoped>
.input-group {
  display: flex;
  justify-content: center;
  margin-bottom: 20px;
}
</style>
