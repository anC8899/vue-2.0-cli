<template>
    <form v-on:submit.prevent="addTodo(newTodo)">
        <div class="form-group">
            <input type="text"
                   class="form-control"
                   v-model="newTodo.title"
            />
        </div>
        <div class="form-group">
            <button class="btn btn-success" type="submit"> Add Todo </button>
        </div>
    </form>
</template>

<script type="text/ecmascript-6">

    export default{
      props: ['todos'],
      data(){
        return {
          newTodo: {id: null, title: '', completed: false}
        }
      },
      methods: {
        addTodo(newTodo){
          this.axios.post('http://fengqi.app/api/todos', {title: this.newTodo.title}).then(response => {
//                console.log(response.data);
            this.todos.push(response.data);
          });

          this.newTodo = {id: null, title: '', completed: false}
        }
      }
    }
</script>
