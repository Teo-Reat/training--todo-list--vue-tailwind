<template>
    <div>
        <router-link to="/">
            <button class="bg-green-400 hover:bg-green-600 active:bg-green-900 text-white font-bold py-2 px-4
            rounded ml-6 mb-6 text-xl">
                To Home
            </button>
        </router-link>
        <add-to-do @add-todo="addToDo"></add-to-do>
        <to-do-list :todos="todos" @delete-todo="deleteToDo"></to-do-list>
    </div>
</template>

<script>
    import ToDoList from "../components/ToDoList";
    import AddToDo from "../components/AddToDo";

    export default {
        components: {
            ToDoList,
            AddToDo
        },
        data() {
            return {
                todos: [],
            }
        },
        mounted() {
            fetch('https://jsonplaceholder.typicode.com/todos?_limit=10')
                .then(response => response.json())
                .then(json => this.todos = json)
        },
        methods: {
            deleteToDo(id) {
                this.todos = this.todos.filter(t => t.id !== id)
            },
            addToDo(data) {
                this.todos.unshift({id: this.Date, title: data, completed: false});
            }
        }
    }
</script>

<style>
    .btn {
        padding: 10px 20px;
    }
</style>