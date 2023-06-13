<template>
  <form @submit="addItem">
    <input type="text" placeholder="New Todo ..." v-model="title"/>
    <input type="submit" value="Add" class="add-btn"/>
  </form>
</template>

<script>
export default {
    name: "AddTodo",
    data() {
        return {
            title: "",
        };
    },
    methods: {
    addItem(event) {
        event.preventDefault();
        const newItem = {
            title: this.title,
            completed: false,
        };
        this.$emit("add-todo", newItem);
        this.title = "";
    },

    // beforCreate() {
    //     console.log("Befor Create" + this.title);
    // },
    // created() {
    //     console.log("Createdddd" + this.title);
    // },
    // beforMount() {
    //     console.log("Befor Mount" + this.title);
    // },
    // mounted() {
    //     console.log("Mounted" + this.title);
    // },
    // beforUnmounted(){
    //     console.log("Befor Destroy" + this.title);
    // },
    // unmounted() {
    //     console.log("Destroyed " + this.title);
    // },

    },
}
</script>

<style scoped>

form{
    display: flex;
}

input[type="text"]{
    flex: 10;
    padding: 5px;
}

input[type="submit"]{
    flex: 2;
}

</style>