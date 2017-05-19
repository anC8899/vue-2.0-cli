<template>
  <div id="app">
    <router-view :todos="todos"></router-view>
  </div>
</template>

<script>
import Todos from './components/Todos.vue'

export default {
  name: 'app',
  data(){
    return {
      todos: [],
    }
  },
  mounted() {
    this.axios.get('http://fengqi.app/api/todos/').then((response) => {
      this.todos = response.data;
//      console.log(response);
    })
  },
  components: {
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2C3E50;
  margin-top: 60px;
}
</style>
