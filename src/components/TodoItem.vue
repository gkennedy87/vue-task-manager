<template>
    <div class="card" v-bind:class = "{'is-complete':todo.completed}"> <!-- adds class of complete if the prop is complete -->
        <ul class="list-group list-group-flush">
            <li class="list-group-item">
                <input type="checkbox" id='checkbox' class="form-check-input" v-on:change="markComplete"/>
                {{todo.title}}
                <button @click ="$emit('del-todo',todo.id)" class="btn btn-danger float-right">Delete</button> <!--emits a function called del-todo with an argument of todo.id -->
            </li>
        </ul>
    </div>
</template>

<script>
export default {
    name: "TodoItem",
    props: [
        "todo"
    ],
    methods: {
        markComplete() {
            console.log("working");
            this.todo.completed = !this.todo.completed; //this changes the current property of the todo to the opposite
        }
    }
}
</script>

<style scoped>
    .todo-item {
        background:#f4f4f4;
        padding: 10px;
        border-bottom: 1px #ccc dotted;
    }
    .is-complete {
        text-decoration: line-through;
    }

    /*.del {
        background: #ff0000;
        color: #fff;
        border:none;
        font-weight: 700;
        padding: 5px 9px;
        border-radius: 50%;
        cursor: pointer;
        float:right;
        
    }*/

    #checkbox {
        border-radius: 10%;
    }
</style>