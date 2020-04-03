<template>
    <div>
        <router-link to="/"><button>Home</button></router-link>
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
                this.todos.push({id: this.Date, title: data, completed: false});
            }
        }
    }
</script>

<style>
    button {
        padding: 10px 20px;
    }
</style>