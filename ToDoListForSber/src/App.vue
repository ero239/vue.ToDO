<template>
  <div id="app">
    <Header/>
    <AddTodo @addTodo="addTodo"/>
    <Todos :todos="todos" @delItem="deleteItem"/>
  </div>
</template>

<script>

import Todos from './components/Todos';
import Header from './components/layout/Header';
import AddTodo from './components/AddTodo';

export default {
  name: 'app',
  components: {
    Todos,
    Header,
    AddTodo
  },
  data() {
    return {
      todos: []
    }
  },
  methods: {
    deleteItem(title) {
      this.todos = this.todos.filter(todo => todo.title !== title)
    },
    addTodo(newTodo) {
      const {title, completed} = newTodo;
      this.todos.push({title,completed});
    }
  },
}
</script>

<style>

* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

body {
  font-family: sans-serif;
  line-height: 20px;
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
