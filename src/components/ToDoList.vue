<template>
    <ul>
        <to-do-item v-for="(todo, i, key) in todos"
                    :key="key"
                    :index="i"
                    :todo="todo"
                    @delete-todo="deleteToDo"></to-do-item>
    </ul>

</template>

<script>
    import ToDoItem from "./ToDoItem";
    export default {
        components: {
            ToDoItem
        },
        props: {
            todos: {
                type: Array,
                required: true
            }
        },
        methods: {
            deleteToDo(id) {
                this.$emit('delete-todo', id)
            }
        }
    }
</script>

<style scoped>
    ul {
        padding: 0;
        margin: 0 auto;
        list-style-type: none;
        width: 600px;
    }
</style>