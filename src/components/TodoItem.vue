<template>
  <div style="display: flex; align-items: center; width: 50%;">
    <h5 style="width: 10%; margin-left: 20px;">{{ todo.id }}</h5>
    <h5 style="width: 80%;">{{ todo.title }}</h5>
    <input style="width: 10%;" type="checkbox" v-model="completed" @change="handleToggleCompleted">
  </div>
</template>

<script>
export default {
  props: {
    todo: Object
  },
  computed: {
    completed: {
      get() {
        return this.todo.completed;
      },
      set(){}
    }
  },
  methods: {
    handleToggleCompleted(event) {
      this.$emit('toggle-completed', this.todo.id, event.target.checked);
    }
  }
}
</script>

<style scoped>
div{
  border: 1px solid black;
}
</style>
