<template>
    <div id="todos">
      <ul class="list-group">
        <li class="list-group-item"
            v-bind:class="{'completed':todo.completed}"
            v-for="(todo , index) in todos">

          <router-link :to="{ name: 'todo', params: { id: todo.id }}">{{todo.title}}</router-link>
            <button class="btn btn-xs pull-right"
                    v-bind:class="[todo.completed ? 'btn-danger':'btn-success']"
                    v-on:click="toggleCompletion(todo)"
            >{{todo.completed ? 'undo' : 'complete'}}
            </button>
            <button class="btn btn-warning btn-xs pull-right"
                    v-on:click="deleteTodo(index,todo)"
            >Del
            </button>
        </li>
    </ul>
    <todo-form :todos="todos"></todo-form>
    </div>
</template>
<style>
    .completed {
      color: green;
      text-decoration: line-through;
    }
</style>
<script type="text/ecmascript-6">
import TodoForm from './TodoForm.vue'
export default{
  name: "todos",
  props: ['todos'],
  methods: {
    deleteTodo(index,todo){

      this.axios.delete('http://fengqi.app/api/todos/' + todo.id).then(response => {
        console.log(response.data);
        this.todos.splice(index, 1);
      });
    },
    toggleCompletion(todo){
      this.axios.patch('http://fengqi.app/api/todos/' + todo.id).then(response => {
                console.log(response.data);
        todo.completed = !todo.completed;
      });

    }
  },
  components: {
    TodoForm
  }
}
</script>
