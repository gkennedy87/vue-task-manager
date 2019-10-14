<template>
    <div>
        <div v-bind:key='todo.id' v-for="todo in todos">
            <!--the todo referenced below is the same as the reference in the for loop above -->
            <TodoItem v-bind:todo="todo" v-on:del-todo="$emit('del-todo',todo.id)"/> <!--forwards/re-emits the del-too function with todo.id -->
        </div>
    </div>
</template>

<script>
import TodoItem from './TodoItem.vue';

export default {
  name: "Todos",
  components: {
      TodoItem
  },
  props: ["todos"]
}


</script>

<style scoped>
  
</style>