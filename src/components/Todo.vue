<template>
    <div>
        <ul class="list-group">
            <li class="list-group-item d-flex justify-content-between align-items-start" v-for="(todo,index) in todos" :key="index">
                <div>
                    {{ todo.name }}
                    <form>
                        <input type="text" class="form-control">
                    </form>
                </div>
                <div>
                    <button class="btn btn-sm btn-primary">Edit</button>
                    &nbsp;
                    <button class="btn btn-sm btn-danger">Delete</button>
                </div>
            </li>
        </ul>
    </div>
</template>
<script>
  export default {
    props: ['todos'],
    data(){
        return {
            isEditing: false,
            newTodoName: ''
        }
    }
  }
</script>

<style scoped>
.completed {
    text-decoration: line-through;
}
</style>