<template>
  <h1>TODO APP</h1>
  <TodoItem v-for="todo in todos" :key="todo.id" :todo="todo" @toggle-completed="handleToggleCompleted">
  </TodoItem>
  <button @click="addTodos()">Add 100 Todos</button>
</template>

<script>
import TodoItem from './components/TodoItem.vue'

export default {
  name: 'App',
  components: {
    TodoItem
  },
  data() {
    return {
      todos: [
        { id: 1, title: 'Install Vue', completed: true },
        { id: 2, title: 'Style app', completed: false },
        { id: 3, title: 'Finish service functionality', completed: false },
        { id: 4, title: 'Setup API', completed: false },
        { id: 5, title: 'Test app', completed: false }
      ]
    };
  },
  methods: {
    handleToggleCompleted(todoId, completed) {
      // Find the todo item with the given id
      const todo = this.todos.find(todo => todo.id === todoId);
      if (todo) {
        // Update the completed status of the todo item
        todo.completed = completed;
      }
    },
    addTodos(){
      for(let i = 0; i < 100; i++){
        this.todos.push({
          id: this.todos.length + 1,
          title: `Todo ${this.todos.length + 1}`,
          completed: false
        });
      }
    }
  }
}
</script>

<style>

</style>
