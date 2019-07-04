<template>
  <div id="app">
    <AddTodo @add-todo="addTodo"/>
    <Todos v-bind:todos="todos" @del-todo="deleteTodo"/>
  </div>
</template>

<script>
import Todos from '../components/Todos.vue';
import AddTodo from '../components/AddTodo.vue';
import axios from 'axios';

export default {
  name: 'Home',
  components: {
    AddTodo,
    Todos,
  },
  data () {
    return {
      todos: []
    }
  },
  methods: {
    deleteTodo(id) {
      // this.todos = this.todos.filter(todo => todo.id !== id);
      axios.delete(`https://jsonplaceholder.typicode.com/todos/${id}`)
      .then(res => this.todos = this.todos.filter(todo => todo.id !== id))
      .catch(err => console.log(err));
    },
    addTodo(newTodo) {
      const { title, completed } = newTodo;

      axios.post('https://jsonplaceholder.typicode.com/todos', {
        title,
        completed
      })
      .then(res => this.todos = [...this.todos, res.data])
      .catch(err => console.log(err));
    }
  },
  created(){
    axios.get('https://jsonplaceholder.typicode.com/todos?_limit=5')
      .then(res => this.todos = res.data)
      .catch(err => console.log(err));
  }
}
</script>

<style>
html {
  box-sizing: border-box;
  font-size: 62.5%;
  margin: 0;
  padding: 0;
}

*, *::before, *::after {
  box-sizing: inherit;
}

body {
  font-size: 1.6rem;
  font-family: Arial, "Helvetica Neue", Helvetica, sans-serif;
  line-height: 1.4;
} 

.btn {
  display: inline-block;
  border: none;
  background: #555;
  color: #fff;
  padding: 7px 20px;
  cursor: pointer;
}

.btn:hover {
  background: #666;
}

</style>
