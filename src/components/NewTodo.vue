<template>
    <div>
        <form @submit.prevent="addTodo">
            <div class="form-group">
            <label for="name"></label>
            <input type="text" v-model="newTodo" id="name" class="form-control">
            </div>
        </form>
    </div>
</template>

<script>
    export default {
        name: "NewTodo",
        data() {
            return {
                newTodo: ''
            }
        },
        methods: {
            addTodo(){
                if(this.newTodo){
                    this.$emit('add-todo',this.newTodo)
                    this.newTodo = ''
                }
            }
        }
    }
</script>

<style scoped>

</style>