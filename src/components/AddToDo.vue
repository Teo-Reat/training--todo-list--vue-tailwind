<template>
    <form>
        <input type="text" v-model="newTodo">
        <button type="submit" @click.prevent="addToDo()">Add ToDo</button>
    </form>
</template>

<script>
    export default {
        data() {
            return {
                newTodo: ''
            }
        },
        methods: {
            addToDo() {
                this.$emit('add-todo', this.newTodo);
                this.newTodo = '';
            }
        }
    }
</script>

<style scoped>
    form {
        display: block;
        margin: 30px auto 40px;
        width: 600px;

    }
    input,
    button {
        padding: 10px 20px;
        box-sizing: border-box;
    }
    input {
        width: 70%;
    }
    button {
        width: 30%;
    }
</style>