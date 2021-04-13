<template>
  <div id="app" class="container">
    <div><h4 class="text-secondary">Options</h4></div>
    <Timer v-bind:order="order"></Timer>
    <AddTodo v-on:add-todo="addTodo" />
    <div><hr></div>
    <draggable v-bind:todos="todos" v-on:del-todo="deleteTodo"></draggable>
  </div>
</template>

<script>
import Timer from '../components/Timer';
import AddTodo from '../components/AddTodo';
import axios from 'axios';
import draggable from '../components/Draggable';
export default {
  name: 'Home',
  components: {
    Timer,
    AddTodo,
    draggable,
  },
  data() {
    return {
      todos: [],
      order: 0
    }
  },
  methods: {
    deleteTodo(id) {
      axios.delete(`https://jsonplaceholder.typicode.com/todos/${id}`)
        .then(res => this.todos = this.todos.filter(todo => todo.id !== id))
        .catch(err => console.log(err));
    },
    addTodo(newTodo) {
      if(!newTodo) return;
      const { title, completed } = newTodo;

      axios.post('https://jsonplaceholder.typicode.com/todos', {
        title,
        completed
      })
        .then(res => this.todos = [...this.todos, res.data])
        .catch(err => console.log(err));
    }
  },
  created() {
    axios.get('https://jsonplaceholder.typicode.com/todos?_limit=5')
      .then(res => this.todos = res.data)
      .catch(err => console.log(err));
  }
}
</script>

<style>
  * {
    box-sizing: border-box;
    margin: 0;
    padding: 0;
  }

  body {
    font-family: Arial, Helvetica, sans-serif;
    line-height: 1.4;

  }

  .btn {
    display: inline-block;
    border: none;
    background: rgb(44, 117, 47);
    color: #fff;
    padding: 7px 20px;
    cursor: pointer;
  }

  .btn:hover {
    background: #666;
  }
</style>
