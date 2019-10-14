<template>
        <form @submit="addTodo" class="form-inline">
            <div class="form-group">
                <label for="title" class="sr-only">Add Task</label>
                <input type="text" name="title" placeholder="Add Task" v-model="title" class="form-control mr-2"> <!-- v-model references the data object in scripts -->
            </div>
            <button type="submit" class="btn btn-primary">Submit</button>
        </form>
</template>

<script>
export default {
    name:"AddTodo",
    data() {
        return {
            title:''
        }
    },
    methods: {
        addTodo(e) {
            e.preventDefault();
            const newTodo = {
                title: this.title, //this is referencing the input. Whatever is typed for the task name is bound to this prop.
                completed: false,
            }
        //send to parent
        this.$emit('add-todo', newTodo); //this is named 'add-todo' and the newTodo prop from addTodo is passed as a parameter
        this.title = '';
        }
    }
}
</script>

<style scoped>
</style>