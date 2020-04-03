<template>
    <li>
        <div>
            <input type="checkbox" @change="todo.completed = !todo.completed">
            <strong class="font-style">{{ index + 1 }}</strong>:
            <span class="font-style" :class="{done: todo.completed}">{{ todo.title }}</span>
        </div>
        <div>
            <button @click="$emit('delete-todo', todo.id)">&times;</button>
        </div>
    </li>
</template>

<script>
    export default {
        props: {
            todo: {
                type: Object,
                required: true
            },
            index: {
                type: Number,
                required: true
            }
        },
        methods: {

        }
    }
</script>

<style scoped>
    li {
        display: flex;
        justify-content: space-between;
        padding: 10px 20px;
    }
    .done {
        text-decoration: line-through;
    }
    .font-style {
        font-size: 26px;
    }
</style>