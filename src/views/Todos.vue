<template>
    <div>
        <router-link to="/">
            <button class="bg-green-400 hover:bg-green-600 active:bg-green-900 text-white font-bold py-2 px-4
            rounded ml-6 mb-6 text-xl">
                To Home
            </button>
        </router-link>
        <add-to-do @add-todo="addToDo"></add-to-do>
        <loader v-if="loading"></loader>
        <to-do-list :todos="todos" @delete-todo="deleteToDo" v-else-if="todos.length"></to-do-list>
        <h3 class="px-4 py-2 w-3/5 mx-auto uppercase tracking-wide font-semibold text-center bg-green-200
        rounded text-blue-900 my-2" v-show="!todos.length">No current assignments</h3>
    </div>
</template>

<script>
    import ToDoList from "../components/ToDoList";
    import AddToDo from "../components/AddToDo";
    import Loader from "../components/Loader";

    export default {
        components: {
            ToDoList,
            AddToDo,
            Loader
        },
        data() {
            return {
                todos: [],
                loading: true
            }
        },
        mounted() {
            fetch('https://jsonplaceholder.typicode.com/todos?_limit=10')
                .then(response => response.json())
                .then(json => {
                    this.todos = json;
                    this.loading = false
                })
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