<template>
    <div id="app">
        <img src="./assets/logo.png">
        <div>
            <TodoList v-bind:todos="todos"></TodoList>
        </div>
        <CreateTodo v-on:create-todo="addTodo"></CreateTodo>

    </div>
</template>

<script>
import TodoList from './components/TodoList';
import CreateTodo from './components/CreateTodo';

export default {
    name: 'app',
    components: {
        TodoList,
        CreateTodo,
    },
    data() {
        return {
            todos: [{
                id: 'Todo1',
                title: 'Todo 1',
                project: 'Todo 1 project',
                done: false,
            }, {
                id: 'Todo2',
                title: 'Todo 2',
                project: 'Todo 2 project',
                done: false,
            }, {
                id: 'Todo3',
                title: 'Todo 3',
                project: 'Todo 3 project',
                done: false,
            }, {
                id: 'Todo4',
                title: 'Todo 4',
                project: 'Todo 4 project',
                done: false,
            }, {
                id: 'Todo5',
                title: 'Todo 5',
                project: 'Todo 5 project',
                done: false,
            }],
        };
    },
    methods: {
        addTodo(newTodo) {
            this.todos.push(newTodo);
        },
    },
};
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
