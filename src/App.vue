<template>
    <div>
      <nav class="navbar bg-dark">

        <Search v-on:query-change="querySearch" />

      </nav>

      <div class="container p-5 mt-5 mb-5 border border-dark" >
        <h3 class="text-center">Agrega, completa y elimina una actividad</h3>
        <TodoAdd v-on:add-todo="addTodo"/>
        <Todos v-bind:todoslist="copyTodos" v-on:delete-todo="deleteTodo" />
      </div>
    </div>
</template>

<script>
import Search from './components/Search.vue'
import Todos from './components/Todos.vue'
import TodoAdd from './components/TodoAdd.vue'

export default {
  name: 'App',
  components: {
    Todos, TodoAdd, Search
  },
  methods: {
    deleteTodo(id){
      this.todos = this.todos.filter(todo => todo.id != id);
      this.copyTodos = [... this.todos];
    },
    addTodo(todo){
      this.todos.push(todo);
      this.copyTodos = [... this.todos];
    },
    querySearch(query){
      if(query.trim() === ''){
        this.copyTodos = [...this.todos];
      }else{
        const temp = this.todos.filter(todo =>{
          return todo.title.includes(query)
        });
        this.copyTodos = [...temp];
      }
    }
  },
  data: () => ({
    todos: [
      {
        id: 0,
        title: 'Ir de compras',
        completed: false
      },
      {
        id: 1,
        title: 'Sacar a pasear al perro',
        completed: true
      },
      {
        id: 2,
        title: 'jugar nintendo',
        completed: false
      },
      {
        id: 3,
        title: 'Hacer la cena',
        completed: true
      }
    ],
    copyTodos: []
  }),
  //se va a ejecutar cuando nuestra app cargue
  created() {
    this.copyTodos = [... this.todos];
  },
}
</script>