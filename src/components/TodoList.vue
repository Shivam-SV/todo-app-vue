<template>
    <ul>
        <li v-for="todo in todos" :key="todo.id">
            <input type="checkbox" v-model="todo.completed">
            <p class="todo-text" :class="{ completed: todo.completed }">{{ todo.text }}</p>
            <button @click="removeTodo(todo.id)">Remove</button>
        </li>
    </ul>
</template>

<script setup>
    import { computed } from 'vue';
    const props = defineProps({
        todos: Array,
        removeTodo: Function
    })
    const todos = computed(() => props.todos);
    const removeTodo = props.removeTodo;
</script>

<style scoped>
    ul {
        list-style: none;
        padding: 0;
    }
    li {
        margin-bottom: 10px;
        display: flex;
        align-items: center;
        box-shadow: 1px 2px 0 2px rgba(100, 100, 100, 0.1);
        padding: .5rem 1rem;
        border-radius: .25rem;
    }
    li > input[type="checkbox"]{
        margin-right: 1rem;
        width: 1.2rem;
        height: 1.2rem;
        accent-color: #c75ec3;
    }
    .todo-text{
        font-size: 1.2rem;
        margin: 0;
        flex-grow: 1;
    }
    button{
        background-color: #c75ec3;
        color: #fff;
        border: none;
        padding: 5px 10px;
        border-radius: 4px;
        cursor: pointer;
        font-size: 1rem;
    }
    .completed{
        text-decoration: line-through;
    }
</style>