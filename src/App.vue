<template>
  <div id="app">
    <!--<img src="./assets/logo.png">-->
<link rel="stylesheet" href="https://cdn.bootcss.com/bootstrap/3.3.7/css/bootstrap.min.css" integrity="sha384-BVYiiSIFeK1dGmJRAkycuHAHRg32OmUcww7on3RYdg4Va+PmSTsz/K68vbdEjh4u" crossorigin="anonymous">
    <!--<hello></hello>-->
    <todos :todos="todos"></todos>
    <todo-form :todos="todos"></todo-form>
  </div>
</template>

<script>
//import Hello from './components/Hello'
import Todos from './components/Todos.vue'
import TodoForm from './components/TodoForm.vue'

export default {
  name: 'app',
  data(){
    return {
      todos: [
        {id: 1, title: 'Learn Vuejs', completed: true}
      ],
    }
  },
  components: {
    Todos,TodoForm
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
</style>
