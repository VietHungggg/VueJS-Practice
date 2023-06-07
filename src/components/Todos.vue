<template>
    <TodoItem v-for="todo in todos" v-bind:key="todo.id" v-bind:todoProps="todo" />
</template>

<script>

import {ref} from "vue"
import TodoItem from "./TodoItem"

export default {
    name: "Top-Todos",
    components: {TodoItem},
    setup() {
        const todos = ref([
            {
                id: 1,
                title: "Todo 1",
                completed: true
            },
            {
                id: 2,
                title: "Todo 2",
                completed: false
            },
            {
                id: 3,
                title: "Todo 3",
                completed: false
            }
        ])
        return {
            todos : todos
        }
    }  
}
</script>

<style>

</style>

// 10m la trang thai ok -> tra ve 3 cai viec 1