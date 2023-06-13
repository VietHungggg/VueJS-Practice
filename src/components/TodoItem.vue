<template>
    <p :class="['todo-item', todoProps.completed ? 'is-completed' : '']">
        <input type='checkbox' :checked = 'todoProps.completed' v-on:change = 'markItemCompleted'/>
        {{ todoProps.title }}
        <button class="del-btn" @click="deleteItem">Delete</button>
    </p>
</template>

<script>

// import { ref } from 'vue'

export default {
    name: "TodoItem",
    props: ["todoProps"],
    methods: {
    markItemCompleted() {
        console.log(this.todoProps);
        this.$emit("item-completed", this.todoProps.id);
    },
    deleteItem() {
        this.$emit("delete-item", this.todoProps.id);
    },
  },
}
</script>

<style>
.todo-item{
    background:#FFF4E0 ;
    padding: 10px;
    margin: 0;
    border-bottom: 1px solid #245953;;
}

.is-completed{
    text-decoration: line-through;
}

.del-btn{
    background: #F15A59;
    color: aliceblue;
    border: none;
    cursor: pointer;
    border-radius: 5px;
    float: right;
}
</style>    