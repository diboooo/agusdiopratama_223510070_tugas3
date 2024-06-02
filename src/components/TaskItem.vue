<template>
    <div>
      <input v-if="isEditing" v-model="editedTask" @keyup.enter="saveTask" />
      <span v-else>{{ task.text }}</span>
      <button @click="isEditing = !isEditing">{{ isEditing ? 'Save' : 'Edit' }}</button>
      <button @click="deleteTask">Delete</button>
    </div>
  </template>
  
  <script>
  export default {
    props: {
      task: Object
    },
    data() {
      return {
        isEditing: false,
        editedTask: this.task.text
      };
    },
    methods: {
      deleteTask() {
        this.$emit('delete-task', this.task.id);
      },
      saveTask() {
        if (this.editedTask.trim()) {
          this.$emit('edit-task', { ...this.task, text: this.editedTask });
          this.isEditing = false;
        }
      }
    }
  };
  </script>
  