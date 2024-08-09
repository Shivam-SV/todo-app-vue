<template>
  <form class="todo-form" @submit.prevent="handleAddTodo">
        <input type="text" v-model="newTodo" placeholder="Add a new todo" />
        <button type="submit">Add</button>
  </form>
</template>

<style scoped>
.todo-form {
    display: flex;
    justify-content: center;
    align-items: center;
    gap: .5rem;
    margin-bottom: 2rem;
}
input {
  border: 1px solid #ccc;
  padding: .5rem;
  font-size: 1rem;
  width: 100%;
  border-radius: .25rem;
}
input:focus {
    border-color: #c83beb;
    outline: none;
    box-shadow: 0 0 0 2px rgba(199, 94, 195, 0.25);
}
button{
  border: none;
  padding: .56rem;
  font-size: 1rem;
  background-color: #c75ec3;
  color: #fff;
  cursor: pointer;
  border-radius: .25rem;
}

</style>

<script setup>
import { ref } from 'vue';
const newTodo = ref('');

const props = defineProps({
    todos: Array,
    addTodo: Function
})

function handleAddTodo() {
    props.addTodo(newTodo.value);
    newTodo.value = '';
}
</script>