<template>
    <div>
      <input v-model="newTask" @keyup.enter="addTask" placeholder="Add a new task" />
      <button @click="addTask">Add Task</button>
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        newTask: ''
      };
    },
    methods: {
      addTask() {
        if (this.newTask.trim()) {
          this.$emit('add-task', this.newTask);
          this.newTask = '';
        }
      }
    }
  };
  </script>
  