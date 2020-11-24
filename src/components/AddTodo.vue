<template>
    <div class="add-todo">
        <form @submit="createNewToDo">
            <input type="text" v-model="title" placeholder="Add To Do...">
            <input type="submit" value="Add" :disabled="isSubmitDisable">
        </form>
    </div>
</template>

<script>

export default {
    name: "AddTodo",
    data () {
        return {
            title: ''
        }
    },
    methods: {
        createNewToDo(e) {
            e.preventDefault()
            const newTodo = {
                title: this.title,
                 completed: false
            }

            this.$emit('add-todo', newTodo)
            this.title = ''
        }
    },
    computed: {
        isSubmitDisable() {
            return this.title.length === 0
        }
    }
}
</script>

<style scoped>
    form {
        display: flex;
    }
    input[type="text"] {
        flex: 10;
        padding: 5px;
    }
    input[type="submit"] {
        flex: 2;
    }
</style>