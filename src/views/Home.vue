<template>
  <div id="home">
    <AddTodo v-on:add-todo="addTodo" />
    <Todos v-bind:todos="todos" v-on:del-todo="deleteTodo" />
  </div>
</template>

<script>
import axios from 'axios';
import Todos from "../components/Todos/Todos";
import AddTodo from "../components/Todos/AddTodo";
export default {
  name: "Home",
  components: {
    Todos,
    AddTodo
  },
  data() {
    return {
      todos: [],
    };
  },
  created() { 
    axios.get('https://jsonplaceholder.typicode.com/todos?_limit=7')
    .then((response) => this.todos  = response.data)
    .catch((err) => console.log(err));
  },
  methods: {
    deleteTodo(id) {
      axios.delete(`https://jsonplaceholder.typicode.com/todos/${id}`)
      .then(() => this.todos = this.todos.filter((todo) => todo.id !== id))
      .catch(err => console.log(err));
    },
    addTodo(newTodo) {
      const {title, completed} = newTodo;
      axios.post('https://jsonplaceholder.typicode.com/todos', {
        title,
        completed
      })
      .then(response => this.todos = [...this.todos, response.data])
      .catch(err => console.log(err));
    }
  },
};
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
  padding: 7px 20px;
  cursor: pointer;
}
.btn-green {
  background: #016898;
  color: #fff;
}
.btn-green:hover {
  background: #19B5FE;
}
</style>
