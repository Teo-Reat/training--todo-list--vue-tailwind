<template>
    <form class="w-3/5 mx-auto flex justify-center mb-6 text-xl shadow">
        <input type="text"
               v-model="newTodo"
               placeholder='New "ToDo" item...'
               class="bg-green-200 box-border py-2 px-4 rounded-l flex-grow min-w-0">
        <button class="bg-green-400 hover:bg-green-600 active:bg-green-900 text-white font-bold py-2 px-4
        rounded-r flex-shrink-0"
                type="submit"
                @click.prevent="addToDo()">
            Add Item
        </button>
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
                if (this.newTodo !== '') {
                    this.$emit('add-todo', this.newTodo);
                    this.newTodo = '';
                } else {
                    this.newTodo = 'Type some text here :)'
                }
            }
        }
    }
</script>

<style scoped>

</style>