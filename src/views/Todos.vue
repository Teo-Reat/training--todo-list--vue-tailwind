<template>
    <div>
        <router-link to="/">
            <button class="bg-green-400 hover:bg-green-600 active:bg-green-900 text-white font-bold py-2 px-4
            rounded ml-6 mb-6 text-xl">
                To Home
            </button>
        </router-link>
        <add-to-do @add-todo="addToDo"></add-to-do>
        <div class="w-3/5 mx-auto text-xl my-6">
            <div class="inline-block relative">
                <select class="block appearance-none w-full bg-white border border-gray-400 hover:border-gray-500
            px-4 py-2 pr-8 rounded shadow leading-tight focus:outline-none focus:shadow-outline bg-green-200
            text-blue-900"
                        v-model="filter">
                    <option>All</option>
                    <option>Completed</option>
                    <option>Uncompleted</option>
                </select>
                <div class="pointer-events-none absolute inset-y-0 right-0 flex items-center px-2 text-gray-700">
                    <svg class="fill-current h-4 w-4" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 20 20">
                        <path d="M9.293 12.95l.707.707L15.657 8l-1.414-1.414L10 10.828 5.757 6.586 4.343 8z"/></svg>
                </div>
        </div>
        </div>
        <loader v-if="loading"></loader>
        <to-do-list :todos="filteredToDos" @delete-todo="deleteToDo" v-else-if="filteredToDos.length"></to-do-list>
        <h3 class="px-4 py-2 w-3/5 mx-auto uppercase tracking-wide font-semibold text-center bg-green-200
        rounded text-blue-900 my-2" v-show="!filteredToDos.length">No current assignments</h3>
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
                loading: true,
                filter: 'All'
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
        },
        computed: {
            filteredToDos() {
                if (this.filter === 'All') {
                    return this.todos
                } else if (this.filter === 'Completed') {
                    return this.todos.filter(t => t.completed)
                } else {
                    return this.todos.filter(t => !t.completed)
                }
            }
        }
    }
</script>

<style>
    .btn {
        padding: 10px 20px;
    }
</style>