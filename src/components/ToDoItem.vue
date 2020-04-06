<template>
    <li @click.prevent="todo.completed = !todo.completed"
        @click.right.prevent="$emit('delete-todo', todo.id)"
        class="cursor-pointer text-blue-900 text-xl px-4 py-2 mt-2 rounded shadow"
        :class="{'bg-green-200': todo.completed, 'bg-blue-200': !todo.completed }">
        <div class="flex justify-between">
            <span class="nselect ml-2 text-blue-900">
                <strong>{{ index + 1 }}. </strong>{{ todo.title | filterTrim }}
            </span>
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
        filters: {
            filterTrim(value) {
                return value.trim()
            }
        },
    }
</script>

<style scoped>
    .nselect::selection {
        background: transparent;
    }
    .nselect::-moz-selection {
        background: transparent;
    }
</style>