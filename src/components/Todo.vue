<template>
    <div>
        <table class="table">
            <thead>
                <tr>
                    <th scope="col">ID</th>
                    <th scope="col">Name</th>
                    <th scope="col">Status</th>
                    <th scope="col">Action</th>
                </tr>
            </thead>
            <tbody>
                <tr v-for="(todo,index) in todos" :key="index">
                    <th>{{ ++index }}</th>
                    <td contenteditable="contenteditable" @blur="$emit('edit', 'id', 'name', $event.target.innerText)">{{ todo.name }}</td>
                    <td>
                        <span v-if="todo.completed"  @click="$emit('toggle',todo)" class="badge badge-success">completed</span>
                        <span v-else  @click="$emit('toggle',todo)" class="badge badge-danger">incomplete</span>
                    </td>
                    <td>
                        <button @click="$emit('delete',todo)" class="btn btn-sm btn-danger">Delete</button>
                    </td>
                </tr>
            </tbody>
        </table>
    </div>
</template>
<script>
  export default {
    props: ['todos'],
}
</script>

<style scoped>
.completed {
    text-decoration: line-through;
}
</style>