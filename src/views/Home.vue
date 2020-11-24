<template>
  <div id="app">
    <AddTodo v-on:add-todo="addNewTodo"/>
    <TodoList v-bind:todos="todos" v-on:del-todo="deleteTodo"/>    
  </div>
</template>

<script>
import TodoList from '../components/TodoList.vue'
import AddTodo from '../components/AddTodo'
import axios from 'axios'

export default {
  name: 'Home',
  components: {
    TodoList,
    AddTodo
  },
  data() {
    return {
      todos: [],
      url: process.env.VUE_APP_API_URL
    }
  },
  methods: {
    deleteTodo(id) {
      axios.delete(`${this.url}/${id}`)
        .then(() => {
          return this.todos = this.todos.filter(todo => todo.id !== id)
        })
        .catch(err => console.log(err))
      
    },
    addNewTodo(newTodo) {
      const { title, completed } = newTodo
      axios.post(this.url, {
        title,
        completed
      })
        .then(res => {
          return this.todos = [...this.todos, res.data]
        })
        .catch(err => console.log(err))
    }
  },
  created() {
    const limit = 5
    axios.get(`${this.url}?_limit=${limit}`)
      .then(res => this.todos = res.data)
      .catch(err => console.log(err))
  }
}
</script>

<style scoped>

</style>

