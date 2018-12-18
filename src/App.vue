<template>
  <div class="app">
    <div class="todo-wrapper">
      <AppHeader></AppHeader>
      <!-- AppHeader is equal to the component insidee the script tag  -->
      <TodoInput v-on:todo:add="addTodo"></TodoInput>
      <!-- when our custom event is ecuted it will ecute the addTodo function insiode the component -->
      <TodoItem v-for="todo in todos" v-bind:todo="todo" v-on:todo:remove="removeTodo" :key="todo.id"></TodoItem>

      <!-- loops through all the todos. Then matches up the props in the todo component   -->
      <!-- v-on listens to todo remove & the removeTodo function -->
    </div>
  </div>
</template>

<script>
import AppHeader from './components/AppHeader.vue';
import TodoInput from './components/TodoInput.vue';
import TodoItem from './components/TodoItem.vue';

export default {
  name: 'App',
  components: {
    AppHeader,
    TodoInput,
    TodoItem
  },
  data() {
    return {
      todos: [
        {id: 0, text: 'make more vue apps'},
        {id: 1, text: 'make a react todo app'},
        {id: 2, text: 'make some sort of ecommerce site'},
      ],
      nextId: 3
    };
  },
  methods: {
    addTodo(text){
      this.todos.push({id: this.nextId, text: text});
      this.nextId++;
    },
    removeTodo(id){
      let todos = this.todos
      this.todos = todos.filter((todo) => todo.id != id)
      // todos is equal to the object above
      // we then filter the todo's withj an if statement making sure they match
    }
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
  margin-top: 60px;
}

.todo-wrapper {
  margin: 20px auto 20px auto;
  width: 500px;
  min-height: 600px;
  border: 5px solid rgba(73, 204, 249, 1.0);
  padding: 20px;
  text-align: center;
  
}
</style>
