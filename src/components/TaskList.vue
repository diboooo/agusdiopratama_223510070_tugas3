<template>
    <div>
      <TaskItem
        v-for="task in tasks"
        :key="task.id"
        :task="task"
        @delete-task="deleteTask"
        @edit-task="editTask"
      />
    </div>
  </template>
  
  <script>
  import TaskItem from './TaskItem.vue';
  
  export default {
    components: {
      TaskItem
    },
    props: {
      tasks: Array
    },
    methods: {
      deleteTask(id) {
        this.$emit('delete-task', id);
      },
      editTask(updatedTask) {
        this.$emit('edit-task', updatedTask);
      }
    }
  };
  </script>
  