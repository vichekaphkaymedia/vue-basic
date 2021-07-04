<template>
  <div>
        <div class="container">
            <div class="card mt-5">
                <div class="card-header">
                All Todos
                </div>
                <div class="card-body">
                <NewTodo @add-todo="addTodo"/>
                <br>
                <ul class="list-group">
                    <todo 
                    :todos="todos"
                    @toggle="toggleToDo"
                    @delete="deleteTodo"
                    />
                </ul>
                </div>
            </div>
        </div>
    </div>
</template>

<script>

import Todo from "./Todo";
import NewTodo from './NewTodo.vue'
import _ from 'lodash';
import axios from 'axios'

export default {
    name: "TodoList",
    components: {
        Todo,
        NewTodo
    },
    data() {
        return {
            todos: []
        }
    },
    mounted(){
        axios.get('./data/todos.json')
        .then(res => {
            // this.todos = todo.data
            this.todos = res.data.map((todo,index) => {
                todo.id = ++index
                return todo
            })
        })
        .catch(err => {
            console.log(err)
        })
    },
    methods: {
        addTodo(name){
            this.todos.push({name: name, completed: false})
        },
        toggleToDo(todo){
            todo.completed = !todo.completed
        },
        editTodo(id,field,text){
            const todoIndex = _.findIndex(this.todos, {
                id: id
            });
            this.appointments[todoIndex][field] = text;
        },
        deleteTodo(todo){
            this.todos = _.without(this.todos,todo)
        }
    }
}
</script>

<style scoped>

</style>