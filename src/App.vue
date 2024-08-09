<script setup>
  import AddTodo from './components/AddTodo.vue';
  import TodoList from './components/TodoList.vue';
  import { ref, watch } from 'vue';

  const todos = ref(JSON.parse(localStorage.getItem('todos') || '[]'));

  function addTodo(newTodo) {
      if (newTodo.trim() === '') return;
      todos.value.push({
          id: Math.random(),
          text: newTodo,
          completed: false
      });
  }

  function removeTodo(id) {
      todos.value = todos.value.filter(todo => todo.id !== id);
  }

  watch(todos, () => {
    localStorage.setItem('todos', JSON.stringify(todos.value));
  }, { deep: true });
</script>

<template>
  <main class="container">
    <AddTodo :todos="todos" :add-todo="addTodo" />
    <TodoList :todos="todos" :remove-todo="removeTodo" />
  </main>
</template>

<style scoped>
.container {
  max-width: 600px;
  margin: 0 auto;
  padding: 1rem;
}
</style>