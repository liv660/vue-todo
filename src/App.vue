<template>
  <div id="app" class="container">
    <TodoInput v-on:addNewTodo="addNewTodo"/>
    <TodoList v-bind:propsTodo="todoItems" v-on:removeTodo="removeTodo" v-on:removeTodoAll="removeTodoAll"/>
  </div>
</template>

<script>
import TodoInput from './components/TodoInput.vue'
import TodoList from './components/TodoList.vue'

export default {
  name: 'app',
  components: {
    'TodoInput':TodoInput,
    'TodoList':TodoList,
  },
  created() {
    if(localStorage.length > 0) {
      for(var i = 0; i < localStorage.length; i++) {
        this.todoItems.push(localStorage.key(i))
      }
    }
  },
  data() {
    return {
        todoItems: [],
    }
  },
  methods: {
    addNewTodo(newTodoItem) {
      localStorage.setItem(newTodoItem, newTodoItem)
      this.todoItems.push(newTodoItem)
    },
    removeTodo(todoItem, idx) {
      localStorage.removeItem(todoItem)
      this.todoItems.splice(idx, 1)
    },
    removeTodoAll() {
      localStorage.clear()
      this.todoItems = []
    }
  },
}
</script>

<style>
.container {
  padding-top: 3%;
}
</style>
