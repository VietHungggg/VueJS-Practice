<template>
    <div>
        <add-todo @add-todo="addTodo"></add-todo>
        <todo-item v-for="todo in todos" 
        :key="todo.id" :todo-props="todo" 
        @item-completed="markComplete" 
        @delete-item="deleteTodo"></todo-item>
    </div>
</template>

<script>

import axios from "axios"
import TodoItem from "./TodoItem"
import AddTodo from "./AddTodo"

export default {
    name: "Top-Todos",
    components: {TodoItem, AddTodo},
    data: function() {
    return {
        todos: [],
    };
    },
    created: function() {
        console.log("Createddddd " + this.title);
        this.getAllTodos();
    },
    methods: {
    getAllTodos: function() {
        var self = this;
        axios
            .get("https://jsonplaceholder.typicode.com/todos?_limit=5")
            .then(function(response) {
            self.todos = response.data;
        })
        .catch(function(error) {
            console.log(error);
        });
    },
    markComplete: function(id) {
        this.todos = this.todos.map(function(todo) {
            if (todo.id === id) {
                todo.completed = !todo.completed;
            }
            return todo;
        });
    },
    deleteTodo: function(id) {
        var self = this;
        axios
            .delete("https://jsonplaceholder.typicode.com/todos/" + id)
            .then(function() {
                self.todos = self.todos.filter(function(todo) {
                    return todo.id !== id;
            });
        })
        .catch(function(error) {
            console.error(error);
        });
    },
    addTodo: function(newTodo) {
        var self = this;
        axios
            .post("https://jsonplaceholder.typicode.com/todos/", newTodo)
            .then(function(response) {
                self.todos.push(response.data);
            })
            .catch(function(error) {
                console.error(error);
            });
        },
    },
    
    // beforCreate() {
    //     console.log("Befor Create ");
    // },
    // beforMount() {
    //     console.log("Befor Mount " + this.title);
    // },
    // mounted() {
    //     console.log("Mounted "  + this.title);
    // },
    // beforeUpdate() {
    //     this.lifecycleStage = 'beforeUpdate ';
    //     console.log('Before Update ' + this.title);
    // },
    // updated() {
    //     this.lifecycleStage = 'updated';
    //     console.log('Updated ' + this.title);
    // },
    // beforUnmounted(){
    //     console.log("Befor Destroy ");
    // },
    // unmounted() {
    //     console.log("Destroyed " + this.title);
    // },

}
</script>

<style>

</style>
