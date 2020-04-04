<template>
    <div>
        <div v-show="todos.length">
            <div class="bg-yellow-200 px-4 py-2 w-3/5 mx-auto uppercase tracking-wide font-semibold text-center
        rounded text-blue-900 my-2">
                Left click to execute, right click to delete
            </div>
            <ul class="w-3/5 mx-auto">
                <to-do-item v-for="(todo, i, key) in todos"
                            :key="key"
                            :index="i"
                            :todo="todo"
                            @delete-todo="deleteToDo"></to-do-item>
            </ul>
        </div>
        <h3 class="px-4 py-2 w-3/5 mx-auto uppercase tracking-wide font-semibold text-center bg-green-200
        rounded text-blue-900 my-2" v-show="!todos.length">No current assignments</h3>
    </div>
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

</style>