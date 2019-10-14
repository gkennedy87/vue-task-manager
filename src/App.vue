<template>
  <div id="app">
    <Navbar />
    <div class="container">
      <div class="card">
        <div class="card-header">Today's Tasks</div>
        <ul class="list-group list-group-flush">
          <li class="list-group-item"><AddTodo v-on:add-todo="addTodo" /></li>
          <li class="list-group-item"><Todos v-bind:todos="todos" v-on:del-todo="deleteTodo" /></li>
        </ul>
      </div>
    </div>
  </div>
</template>

<script>
import Navbar from './components/layout/Navbar';

import Todos from './components/Todos';
import AddTodo from './components/AddTodo';
import axios from 'axios';
export default {
  name: 'app',
  components: {
    Navbar,
    Todos,
    AddTodo
  },
  data() {
    return {
      todos: []
    }
  },
  methods: {
    deleteTodo(id) {
      axios.delete(`https://jsonplaceholder.typicode.com/todos/${id}`)
        .then(res=> this.todos = this.todos.filter(todo => todo.id !== id))
        .catch(err=>console.log(err));
      
    },
    addTodo(newTodo) {

      const { title, completed} = newTodo;
      axios.post('https://jsonplaceholder.typicode.com/todos', {title, completed})
        .then(res => this.todos = [...this.todos, res.data] )
        .catch(err => console.log(err));

      ;
    }
  },
  created() {
    axios.get('https://jsonplaceholder.typicode.com/todos?_limit=7')  //use axios to get data from API url
      .then(res => this.todos = res.data) // returns a promise which is handled with .then(), res is the response object
      .catch(err => console.log(err)); //catches and logs error
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
 
}

</style>
