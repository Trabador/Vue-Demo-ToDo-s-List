<template>
    <div class="todo-item">
        <p v-bind:class="{'is-complete': todo.completed}">
            <input type="checkbox"  v-model="todo.completed">
            {{todo.title}}
            <button @click="$emit('del-todo', todo.id)" :disabled="todo.completed === false">X</button>
        </p>
    </div>
</template>

<script>
export default {
    name: "TodoItem",
    props: ["todo"],
}
</script>

<style scoped>
    .is-complete{
        text-decoration: line-through;
    }

    .todo-item{
        display: flex;
        justify-content: space-between;
    }
</style>