<template>
    <div>
        <p>Completed tasks : {{todos.filter(todo=> {return todo.done === true}).length}}</p>
        <p>Pending tasks : {{todos.filter(todo=> {return todo.done === false}).length}}</p>
        <Todo v-for="todo in todos" v-bind:todo="todo" :todo.sync="todo" :key="todo.id" v-on:delete-todo="deleteTodo(todo)" v-on:complete-todo="completeTodo(todo)"></Todo>
    </div>
</template>

<script type="text/javascript" >

import Todo from './Todo';

export default {
    props: ['todos'],
    components: {
        Todo,
    },
    methods: {
        deleteTodo(todo) {
            const todoIndex = this.todos.indexOf(todo);
            this.todos.splice(todoIndex, 1);
        },
        completeTodo(todo) {
            const todoIndex = this.todos.indexOf(todo);
            this.todos[todoIndex].done = true;
        },
    },
};
</script>

<style>
</style>
