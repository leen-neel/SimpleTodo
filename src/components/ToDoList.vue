<template>
    
    <div class="container">
        <div class="row">
            <div class="col-12">
                <p class="display-3">
                    Todo List App
                </p>
            </div>
        </div>

        <div class="row">
            <new-todo 
            @on-addtodo="addTodo($event)"
            />
        </div>

        <div class="row">
            <div class="col-12 col-lg-6">
                <ul class="list-group">
                    <ToDo v-for="(todo, index) in todos" 
                    :key="index"
                    :todoString="todo.todoString"
                    :completed="todo.completed"
                    @on-delete="deleteTodo(todo)"
                    @on-toggle="toggleTodo(todo)"
                    @on-edit="editTodo(todo, $event)"
                    />
                </ul>
            </div>
        </div>

    </div>
</template>

<script>

import ToDo from './ToDo.vue'
import NewTodo from './NewToDo.vue'

export default {

    components: {
        ToDo,
        NewTodo
    },

    data() {
        return {
            todos: [
                {todoString: "Make Angular Course", completed: false},
                {todoString: "Drink milk", completed: true},
                {todoString: "Slap bass", completed: true},
            ]
        }
    },
    methods: {
        addTodo(newTodo){
            this.todos.push({
                todoString: newTodo, completed: false
            })
        },

        toggleTodo(todo){
            todo.completed = !todo.completed;
        },

        editTodo(todo, newTodoString){
            todo.todoString = newTodoString
        },

        deleteTodo(deleteTodo) {
            this.todos = this.todos.filter(
                 todo => todo.todoString !== deleteTodo.todoString
            )
        }
    }
}
</script>

<style>

</style>
