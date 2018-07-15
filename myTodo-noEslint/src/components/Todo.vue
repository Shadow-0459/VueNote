<template>
    <div>
        <div class="card">
            <div class="content" v-show="!isEditing">
                <div class="title">
                    {{todo.title}}
                </div>
                <div class="project">
                    {{todo.project}}
                </div>
                <div class="functions">
                    <span class="w3-button w3-white w3-border w3-border-red form-function" v-on:click="showForm">edit</span>
                    <span class="w3-button w3-white w3-border w3-border-red form-function" v-on:click="deleteTodo(todo)">delete</span>
                </div>
            </div>
            <div class="content" v-show="isEditing">
                <div class="form">
                    <div class="field">
                        <label>Title</label>
                        <input class="form-input" type="text" v-model="todo.title"></input>
                    </div>
                    <div class="field">
                        <label>Project</label>
                        <input class="form-input" type="text" v-model="todo.project"></input>
                    </div>
                    <button class="carry-out" v-on:click="hideForm">Submit</button>
                </div>
            </div>
            <button class="carry-out" v-show="!isEditing && todo.done">Completed !</button>
            <button class="carry-out" v-show="!isEditing && !todo.done" v-on:click="completeTodo(todo)">Complete</button>
        </div>
    </div>
</template>

<script type="text/javascript" >
    export default {
        props: ['todo'],
        data() {
            return {
                isEditing: false,
            }
        },
        methods: {
            showForm() {
                this.isEditing = true;
            },
            hideForm() {
                this.isEditing = false;
            },
            deleteTodo(todo) {
                this.$emit('delete-todo', todo);
            },
            completeTodo(todo) {
                this.$emit('complete-todo', todo);
            },
        },
    };
</script>

<style>
.card {
    border: 1px solid;
    width: 200px;
    height: 110px;
    float: left;
    margin-left: 3%;
    margin-right: 3%;
    margin-top: 20px;
}
.form-function {
    height: 20px;
    line-height: 5px;
}
.carry-out {
    margin-top: 5px;
}
</style>
