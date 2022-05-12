<template>
  <div id="app">
    <todo-header></todo-header>
    <todo-input @addTodo="addTodo"></todo-input>
    <todo-list :tododata="todos" @removeTodo="removeTodo" @toggleTodo="toggleTodo"></todo-list>
    <todo-footer @clearAll="clearAll"></todo-footer>
  </div>
</template>

<script>
import TodoHeader from './components/TodoHeader.vue'
import TodoInput from './components/TodoInput.vue'
import TodoList from './components/TodoList.vue'
import TodoFooter from './components/TodoFooter.vue'

export default {
  name: 'App',
  data: () => {
  // data() { // 화살표도 귀찮다면
    return {
      todos: [],
    }
  },
  methods: {
    addTodo(item) {
      const todoObj = {
        // item: item,
        item,
        completed: false,
      }
      localStorage.setItem(item, JSON.stringify(todoObj))
      this.todos.push(todoObj)
    },
    removeTodo(todoItem, idx) {
      localStorage.removeItem(todoItem)
      this.todos.splice(idx, 1)
    },
    // toggleTodo(todo) {
    toggleTodo(idx) {
      this.todos[idx].completed = !this.todos[idx].completed
      // todo.completed = !todo.completed

      localStorage.removeItem(this.todos[idx].item)
      // localStorage.removeItem(todo.item)
      localStorage.setItem(this.todos[idx].item, JSON.stringify(this.todos[idx]))
      // localStorage.setItem(todo.item, JSON.stringify(todo))
    },
    clearAll() {
      localStorage.clear();
      this.todos = []
    }
  },
  components: {
    TodoHeader,
    TodoInput,
    TodoList,
    TodoFooter
  },
  created() {
    if(localStorage.length > 0) {
      for(var i = 0; i < localStorage.length; i++) {
        console.log(localStorage.key(i))

        const todoItem = localStorage.getItem(localStorage.key(i))
        this.todos.push(JSON.parse(todoItem))
      }
    }
  },
}
</script>

<style>
  body {
    background-color: #f6f6f6;
    text-align: center;
  }
</style>
