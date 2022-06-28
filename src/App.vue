<template>  
  
  <div class id="app">
    <div class="container grid-xs py-2">      
      <img class="img-resposive img-logo" src="@/assets/logo.png" alt="Logomarca da SwitchCase" srcset="">
      <form @submit.prevent="addTodo(todo)">
        <div class="input-group" >
        <input type="text" v-model="todo.description" class="form-input" placeholder="Novo todo">
        <button class="btn btn-primary input-group-btn">Adiciona</button>        
      </div>        
      </form>
      <div class="todo-list " v-if="todos.length">
        <Todo v-for="t in todos" :key="t.id"  @toggle="toggleTodo" :todo="t"/>
      </div>
    </div>
  </div>
 
</template>

<script>
import Todo from './components/Todo.vue';





export default {
    name: "App",
    data() {
        return { todos: [], todo: { checked: false } };
    },
    methods: {
        addTodo(todo) {
            todo.id = Date.now();
            this.todos.push(todo);
            this.todo = { checked: false };
        },
        toggleTodo(todo){
          const index = this.todos.findIndex(item => item.id === todo.id);
          console.log(index)
          if(index > -1){
            this.todos[index].checked = !this.todos[index].checked;            
          }

        }
    },
    components: { Todo }
}
</script>


<style scoped>
.img-logo{
    max-width: 200px;
    margin: 0 auto;
}
.todo-list{
  padding-top: 2rem;
}



</style>

