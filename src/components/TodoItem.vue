<template>
    <p :class="['todo-item', todoProps.completed ? 'is-completed' : '']">
        <input type='checkbox' :checked = 'todoProps.completed'/>
        {{ todoProps.title }}
        <button class="del-btn">Delete</button>
    </p>
</template>

<script>
export default {
    name: "TodoItem",
    props: ["todoProps"],
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