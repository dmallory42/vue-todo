<template>
  <div id="app">
    <h1>{{title}}:</h1>
    <input type="text" class="nes-input" placeholder="Add todo.." v-on:keyup.enter="addTodo">
    <ul class="todo-ul">
      <div v-if="todos.length === 0">Great job. Take a break!</div>
      <todo-item
        v-for="todo in sortedTodos"
        v-bind:key="todo.text"
        v-bind:text="todo.text"
        v-bind:done.sync="todo.done"
        v-bind:id="todo.id"
        v-on:removeTodo="removeTodo">
      </todo-item>
    </ul>
  </div>
</template>

<script>
import TodoItem from "@/components/ui/TodoItem";

export default {
  name: 'App',
  components: {TodoItem},
  data: function () {
    return {
      todos: [
        { text: 'todo 1', done: true, id: Date.now()},
        { text: 'todo 2', done: false, id: Date.now() + 1},
        { text: 'todo 3', done: false, id: Date.now() + 2},
      ],
      title: 'To-Do List'
    }
  },
  computed: {
    sortedTodos: function() {
      let todos = this.todos
      return todos.sort((a, b) => a.done - b.done)
    }
  },
  methods: {
    addTodo(event) {
      const text = event.target.value
      this.todos.push({text, done: false, id: Date.now()})
      event.target.value = ''
    },
    removeTodo(id) {
      this.todos = this.todos.filter(todo => todo.id !== id)
    }
  }
}
</script>

<style>
  @import '../node_modules/nes.css/css/nes-core.min.css';
  @import './assets/styles/app.css';
</style>
