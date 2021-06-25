<template>
  <div>
        <div class="container">
            <div class="card mt-5">
                <div class="card-header">
                Add New Todo
                </div>
                <div class="card-body">
                <form>
                    <div class="form-group">
                    <label for="name"></label>
                    <input type="text" id="name" class="form-control">
                    </div>
                </form>
                <br>
                <ul class="list-group">
                    <todo 
                    :todos="todos" 
                    @on-delete="deleteTodo"
                    @on-toggle="toggleToDo"
                    @on-edit="editTodo($event)"
                    />
                </ul>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
import Todo from "./Todo";
export default {
  name: "TodoList",
  components: {
      Todo
  },
  data() {
    return {
      todos: [
        {name: "Todo 001",completed: false},
        {name: "Todo 002",completed: false},
        {name: "Todo 003",completed: false},
        {name: "Todo 004",completed: false}
      ]
    }
  },
  methods: {
    addTodo(name){
      this.todos.push({name: name, completed: false})
    },
    toggleToDo(todo){
      todo.completed = !todo.completed
    },
    editTodo(newTodoString){
        this.todos = newTodoString
    },
    deleteTodo(deleteTodo){
      this.todos = this.todos.filter(todo => todo.name !== deleteTodo)
    }
  }
}
</script>

<style scoped>

</style>